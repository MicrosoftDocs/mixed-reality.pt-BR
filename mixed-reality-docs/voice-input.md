---
title: Entrada de voz
description: A entrada de voz é uma entrada principal para o HoloLens e os headsets de imersão de realidade mista do Windows. A voz pode ser usada para comandos, ditado, Cortana e muito mais.
author: Hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv, voz, Cortana, fala, entrada
ms.openlocfilehash: f2ae18d4063c7c4a63346a1202cacaa7fbbdf959
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723185"
---
# <a name="voice-input"></a><span data-ttu-id="396a3-105">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="396a3-105">Voice input</span></span>

![Entrada de voz](images/UX/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="396a3-107">A voz é uma das principais formas de entrada no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="396a3-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="396a3-108">Ele permite que você comando diretamente um holograma sem precisar usar [gestos de mão](gaze-and-commit.md#composite-gestures).</span><span class="sxs-lookup"><span data-stu-id="396a3-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="396a3-109">A entrada de voz pode ser uma maneira natural de comunicar sua intenção.</span><span class="sxs-lookup"><span data-stu-id="396a3-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="396a3-110">A voz é especialmente boa na passagem de interfaces complexas, pois permite que os usuários recortem os menus aninhados com um único comando.</span><span class="sxs-lookup"><span data-stu-id="396a3-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="396a3-111">A entrada de voz é alimentada pelo [mesmo mecanismo](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) que dá suporte à fala em todos os outros _aplicativos universais do Windows_.</span><span class="sxs-lookup"><span data-stu-id="396a3-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other _Universal Windows Apps_.</span></span> <span data-ttu-id="396a3-112">No HoloLens, o reconhecimento de fala sempre funcionará na linguagem de exibição do Windows configurada em configurações.</span><span class="sxs-lookup"><span data-stu-id="396a3-112">On HoloLens, speech recognition will always function in the Windows display language configured in Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="396a3-113">Voz e olhar</span><span class="sxs-lookup"><span data-stu-id="396a3-113">Voice and gaze</span></span>

<span data-ttu-id="396a3-114">Ao usar comandos de voz, o olhar normalmente é usado como o mecanismo de direcionamento, seja com um cursor ("Select") ou para canalizar implicitamente o comando para um aplicativo que você está vendo.</span><span class="sxs-lookup"><span data-stu-id="396a3-114">When using voice commands, (head or eye) gaze is typically used as the targeting mechanism, whether with a cursor ("select") or to implicitly channel your command to an application that you are looking at.</span></span> <span data-ttu-id="396a3-115">Para isso, talvez nem seja necessário mostrar qualquer cursor olhar _("vê-lo, digamos")_ .</span><span class="sxs-lookup"><span data-stu-id="396a3-115">For this, it may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="396a3-116">É claro que alguns comandos de voz não exigem um destino, como "ir para iniciar" ou "Ei Cortana".</span><span class="sxs-lookup"><span data-stu-id="396a3-116">Of course, some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="396a3-117">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="396a3-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="396a3-118"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="396a3-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="396a3-119"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="396a3-119"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="396a3-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="396a3-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="396a3-121"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="396a3-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="396a3-122">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="396a3-122">Voice input</span></span></td>
        <td><span data-ttu-id="396a3-123">✔️</span><span class="sxs-lookup"><span data-stu-id="396a3-123">✔️</span></span></td>
        <td><span data-ttu-id="396a3-124">✔️</span><span class="sxs-lookup"><span data-stu-id="396a3-124">✔️</span></span></td>
        <td><span data-ttu-id="396a3-125">✔️ (com microfone)</span><span class="sxs-lookup"><span data-stu-id="396a3-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="396a3-126">O comando "Select"</span><span class="sxs-lookup"><span data-stu-id="396a3-126">The "select" command</span></span>

<span data-ttu-id="396a3-127">**HoloLens (1ª geração)**</span><span class="sxs-lookup"><span data-stu-id="396a3-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="396a3-128">Mesmo sem adicionar especificamente suporte de voz ao seu aplicativo, os usuários podem ativar os hologramas simplesmente dizendo o comando de voz do sistema "Select".</span><span class="sxs-lookup"><span data-stu-id="396a3-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="396a3-129">Isso se comporta da mesma forma que um [toque de ar](gaze-and-commit.md#composite-gestures) no HoloLens, pressionando o botão Selecionar no [clicador de HoloLens](hardware-accessories.md#hololens-clicker)ou pressionando o gatilho em um [controlador de movimento de realidade mista do Windows](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="396a3-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="396a3-130">Você ouvirá um som e verá uma dica de ferramenta com "Select" aparecer como confirmação.</span><span class="sxs-lookup"><span data-stu-id="396a3-130">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="396a3-131">"Selecionar" é habilitado por um algoritmo de detecção de palavra-chave de baixo consumo de energia para que ele esteja sempre disponível para você, a qualquer momento, com impacto mínimo na vida útil da bateria, mesmo com suas mãos no seu lado.</span><span class="sxs-lookup"><span data-stu-id="396a3-131">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="396a3-132">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="396a3-132">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="396a3-133">Para usar o comando de voz "Select" no HoloLens 2, primeiro você precisa abrir o cursor olhar para usar como um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="396a3-133">In order to use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="396a3-134">O comando para trazê-lo é fácil de lembrar, apenas digamos, "Select".</span><span class="sxs-lookup"><span data-stu-id="396a3-134">The command to bring it up is easy to remember -- just say, "select".</span></span><br><br>
        <span data-ttu-id="396a3-135">Para sair do modo, basta usar suas mãos novamente, seja pelo ar tocando, abordando um botão com seus dedos ou usando o gesto do sistema.</span><span class="sxs-lookup"><span data-stu-id="396a3-135">To exit the mode, simply use your hands again, either by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br>
        <span data-ttu-id="396a3-136">*Imagem: Diga "selecionar" para usar o comando de voz para seleção*</span><span class="sxs-lookup"><span data-stu-id="396a3-136">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![Um usuário pode dizer "selecionar" para usar o comando de voz para uma seleção.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a><span data-ttu-id="396a3-138">Ei Cortana</span><span class="sxs-lookup"><span data-stu-id="396a3-138">Hey Cortana</span></span>

<span data-ttu-id="396a3-139">Você também pode dizer "Ei Cortana" para abrir a Cortana a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="396a3-139">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="396a3-140">Você não precisa esperar que ela pareça continuar perguntando sua pergunta ou dando a ela uma instrução. por exemplo, tente dizer "Ei Cortana, qual é o clima?"</span><span class="sxs-lookup"><span data-stu-id="396a3-140">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="396a3-141">como uma única frase.</span><span class="sxs-lookup"><span data-stu-id="396a3-141">as a single sentence.</span></span> <span data-ttu-id="396a3-142">Para obter mais informações sobre a Cortana e o que você pode fazer, basta perguntar a ela!</span><span class="sxs-lookup"><span data-stu-id="396a3-142">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="396a3-143">Diga "Ei Cortana, o que eu posso dizer?"</span><span class="sxs-lookup"><span data-stu-id="396a3-143">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="396a3-144">e ela receberá uma lista de comandos de trabalho e sugeridos.</span><span class="sxs-lookup"><span data-stu-id="396a3-144">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="396a3-145">Se você já estiver no aplicativo Cortana, também poderá clicar no botão **?**</span><span class="sxs-lookup"><span data-stu-id="396a3-145">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="396a3-146">na barra lateral para extrair esse mesmo menu.</span><span class="sxs-lookup"><span data-stu-id="396a3-146">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="396a3-147">**Comandos específicos do HoloLens**</span><span class="sxs-lookup"><span data-stu-id="396a3-147">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="396a3-148">"O que posso falar?"</span><span class="sxs-lookup"><span data-stu-id="396a3-148">"What can I say?"</span></span>
* <span data-ttu-id="396a3-149">"Ir para o início"-em vez de [cair](system-gesture.md#bloom) para chegar ao [menu iniciar](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="396a3-149">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="396a3-150">"Iniciar <app>"</span><span class="sxs-lookup"><span data-stu-id="396a3-150">"Launch <app>"</span></span>
* <span data-ttu-id="396a3-151">"Mover <app> aqui"</span><span class="sxs-lookup"><span data-stu-id="396a3-151">"Move <app> here"</span></span>
* <span data-ttu-id="396a3-152">"Tirar uma foto"</span><span class="sxs-lookup"><span data-stu-id="396a3-152">"Take a picture"</span></span>
* <span data-ttu-id="396a3-153">"Iniciar gravação"</span><span class="sxs-lookup"><span data-stu-id="396a3-153">"Start recording"</span></span>
* <span data-ttu-id="396a3-154">"Parar gravação"</span><span class="sxs-lookup"><span data-stu-id="396a3-154">"Stop recording"</span></span>
* <span data-ttu-id="396a3-155">"Aumentar o brilho"</span><span class="sxs-lookup"><span data-stu-id="396a3-155">"Increase the brightness"</span></span>
* <span data-ttu-id="396a3-156">"Diminuir o brilho"</span><span class="sxs-lookup"><span data-stu-id="396a3-156">"Decrease the brightness"</span></span>
* <span data-ttu-id="396a3-157">"Aumentar o volume"</span><span class="sxs-lookup"><span data-stu-id="396a3-157">"Increase the volume"</span></span>
* <span data-ttu-id="396a3-158">"Diminuir o volume"</span><span class="sxs-lookup"><span data-stu-id="396a3-158">"Decrease the volume"</span></span>
* <span data-ttu-id="396a3-159">"Mudo" ou "desativar mudo"</span><span class="sxs-lookup"><span data-stu-id="396a3-159">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="396a3-160">"Desligar o dispositivo"</span><span class="sxs-lookup"><span data-stu-id="396a3-160">"Shut down the device"</span></span>
* <span data-ttu-id="396a3-161">"Reiniciar o dispositivo"</span><span class="sxs-lookup"><span data-stu-id="396a3-161">"Restart the device"</span></span>
* <span data-ttu-id="396a3-162">"Ir para o estado de suspensão"</span><span class="sxs-lookup"><span data-stu-id="396a3-162">"Go to sleep"</span></span>
* <span data-ttu-id="396a3-163">"Qual é o tempo?"</span><span class="sxs-lookup"><span data-stu-id="396a3-163">"What time is it?"</span></span>
* <span data-ttu-id="396a3-164">"A quantidade de bateria que resta?"</span><span class="sxs-lookup"><span data-stu-id="396a3-164">"How much battery do I have left?"</span></span>



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="396a3-165">"Vê-lo, digamos"</span><span class="sxs-lookup"><span data-stu-id="396a3-165">"See It, Say It"</span></span><br>
        <span data-ttu-id="396a3-166">O HoloLens tem um modelo "vê-lo, digamos" para entrada de voz, em que os rótulos nos botões informam aos usuários quais comandos de voz eles podem dizer também.</span><span class="sxs-lookup"><span data-stu-id="396a3-166">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="396a3-167">Por exemplo, ao examinar uma janela de aplicativo no HoloLens (1º gen), um usuário pode dizer o comando "ajustar" que eles veem na barra de aplicativos para ajustar a posição do aplicativo no mundo.</span><span class="sxs-lookup"><span data-stu-id="396a3-167">For example, when looking at an app window in HoloLens (1st gen), a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="396a3-168">*Imagem: um usuário pode dizer o comando "ajustar" que vê na barra de aplicativos para ajustar a posição do aplicativo*</span><span class="sxs-lookup"><span data-stu-id="396a3-168">*Image: A user can say the "Adjust" command which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="396a3-169">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="396a3-169">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="396a3-170">![ao examinar uma janela de aplicativo ou um holograma, um usuário pode dizer o comando "ajustar" que vê na barra de aplicativos para ajustar a posição do aplicativo no mundo](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="396a3-170">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        <span data-ttu-id="396a3-171">Quando os aplicativos seguem essa regra, os usuários podem entender facilmente o que dizer para controlar o sistema.</span><span class="sxs-lookup"><span data-stu-id="396a3-171">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="396a3-172">Para reforçar isso, enquanto nuvens em um botão no HoloLens (1º gen), você verá uma dica de ferramenta de "pesquisa de voz" que aparecerá após um segundo se o botão estiver habilitado para voz e exibirá o comando para falar para "pressionar".</span><span class="sxs-lookup"><span data-stu-id="396a3-172">To reinforce this, while gazing at a button in HoloLens (1st gen), you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="396a3-173">Para revelar as dicas de ferramenta de voz no HoloLens 2, mostre o cursor de voz dizendo "Select" ou "o que eu posso dizer" (consulte a imagem).</span><span class="sxs-lookup"><span data-stu-id="396a3-173">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="396a3-174">*Imagem: "vê-lo, digamos", os comandos aparecem abaixo dos botões*</span><span class="sxs-lookup"><span data-stu-id="396a3-174">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![Vê-lo, digamos que os comandos de ti apareçam abaixo dos botões](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="396a3-176">Comandos de voz para manipulação rápida de holograma</span><span class="sxs-lookup"><span data-stu-id="396a3-176">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="396a3-177">Há vários comandos de voz que você pode dizer enquanto nuvens em um holograma para executar rapidamente tarefas de manipulação.</span><span class="sxs-lookup"><span data-stu-id="396a3-177">There are a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="396a3-178">Esses comandos de voz funcionam em janelas de aplicativos, bem como em objetos 3D que você colocou no mundo.</span><span class="sxs-lookup"><span data-stu-id="396a3-178">These voice commands work on app windows as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="396a3-179">**Comandos de manipulação de holograma**</span><span class="sxs-lookup"><span data-stu-id="396a3-179">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="396a3-180">Entre em frente</span><span class="sxs-lookup"><span data-stu-id="396a3-180">Face me</span></span>
* <span data-ttu-id="396a3-181">Maior | Aprimorou</span><span class="sxs-lookup"><span data-stu-id="396a3-181">Bigger | Enhance</span></span>
* <span data-ttu-id="396a3-182">Menor</span><span class="sxs-lookup"><span data-stu-id="396a3-182">Smaller</span></span>

<span data-ttu-id="396a3-183">No HoloLens 2, você também pode criar interações mais naturais em combinação com olhar, que implicitamente fornece informações contextuais sobre o que você está referindo.</span><span class="sxs-lookup"><span data-stu-id="396a3-183">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="396a3-184">Por exemplo, você poderia simplesmente olhar para um holograma e dizer "colocar _isso_" e, em seguida, examinar onde deseja colocá-lo e dizer " _aqui_".</span><span class="sxs-lookup"><span data-stu-id="396a3-184">For example, you could simply look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="396a3-185">Ou você pode examinar uma parte Holographic em um computador complexo e dizer: "Dê-me mais informações sobre _isso_".</span><span class="sxs-lookup"><span data-stu-id="396a3-185">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>



## <a name="discovering-voice-commands"></a><span data-ttu-id="396a3-186">Descobrindo comandos de voz</span><span class="sxs-lookup"><span data-stu-id="396a3-186">Discovering voice commands</span></span>

<span data-ttu-id="396a3-187">Alguns comandos, como os comandos para manipulação rápida acima, podem ser ocultados.</span><span class="sxs-lookup"><span data-stu-id="396a3-187">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="396a3-188">Para saber mais sobre os comandos que você pode usar, olhar em um objeto e, por exemplo, "o que eu posso dizer?".</span><span class="sxs-lookup"><span data-stu-id="396a3-188">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="396a3-189">Uma lista de comandos possíveis é exibida.</span><span class="sxs-lookup"><span data-stu-id="396a3-189">A list of possible commands pops up.</span></span> <span data-ttu-id="396a3-190">Você também pode usar o cursor olhar de cabeçalho para examinar e revelar as dicas de ferramenta de voz para cada botão na frente de você.</span><span class="sxs-lookup"><span data-stu-id="396a3-190">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="396a3-191">Se você quiser uma lista completa, basta dizer "Mostrar todos os comandos" a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="396a3-191">If you want a complete list, just say, "Show all commands" anytime.</span></span> 


## <a name="dictation"></a><span data-ttu-id="396a3-192">Ditado</span><span class="sxs-lookup"><span data-stu-id="396a3-192">Dictation</span></span>

<span data-ttu-id="396a3-193">Em vez de digitar com [toques de ar](gaze-and-commit.md#composite-gestures), o ditado de voz pode ser mais eficiente para inserir texto em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="396a3-193">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="396a3-194">Isso pode acelerar muito a entrada com menos esforço para o usuário.</span><span class="sxs-lookup"><span data-stu-id="396a3-194">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="396a3-195">![ditado de voz começa selecionando o botão de microfone](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="396a3-195">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="396a3-196">*O ditado de voz começa selecionando o botão de microfone no teclado*</span><span class="sxs-lookup"><span data-stu-id="396a3-196">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="396a3-197">Sempre que o teclado Holographic estiver ativo, você poderá alternar para o modo de ditado em vez de digitar.</span><span class="sxs-lookup"><span data-stu-id="396a3-197">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="396a3-198">Selecione o microfone no lado da caixa de entrada de texto para começar.</span><span class="sxs-lookup"><span data-stu-id="396a3-198">Select the microphone on the side of the text input box to get started.</span></span>


## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="396a3-199">Adicionando comandos de voz ao seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="396a3-199">Adding voice commands to your app</span></span>

<span data-ttu-id="396a3-200">Considere a adição de comandos de voz em qualquer experiência que você criar.</span><span class="sxs-lookup"><span data-stu-id="396a3-200">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="396a3-201">A voz é uma maneira poderosa e conveniente de controlar o sistema e os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="396a3-201">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="396a3-202">Como os usuários falam com uma variedade de dialetos e sotaques, a escolha adequada das palavras garantirá que os comandos sejam interpretados de maneira inequívoca.</span><span class="sxs-lookup"><span data-stu-id="396a3-202">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="396a3-203">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="396a3-203">Best practices</span></span>

<span data-ttu-id="396a3-204">A seguir, algumas práticas que auxiliarão em um reconhecimento de fala perfeito.</span><span class="sxs-lookup"><span data-stu-id="396a3-204">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="396a3-205">**Use comandos concisos** - quando possível, escolha palavras com duas ou mais sílabas.</span><span class="sxs-lookup"><span data-stu-id="396a3-205">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="396a3-206">Palavras com uma sílaba tendem a empregar sons de vogais diferentes quando faladas por pessoas com sotaques diferentes.</span><span class="sxs-lookup"><span data-stu-id="396a3-206">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="396a3-207">Exemplo: "reproduzir vídeo" é melhor do que "reproduzir o vídeo selecionado no momento"</span><span class="sxs-lookup"><span data-stu-id="396a3-207">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="396a3-208">**Usar vocabulário simples** -exemplo: "mostrar nota" é melhor do que "mostrar letreiro"</span><span class="sxs-lookup"><span data-stu-id="396a3-208">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="396a3-209">**Certifique-se de que os comandos não sejam destrutivos** - certifique-se de que as ações que podem ser executadas por um comando de voz não sejam destrutivas e possam ser facilmente desfeitas caso outra pessoa falando nas proximidades do usuário acidentalmente acione um comando.</span><span class="sxs-lookup"><span data-stu-id="396a3-209">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="396a3-210">**Evite comandos com sons semelhantes** - evite registrar vários comandos de fala muito semelhantes.</span><span class="sxs-lookup"><span data-stu-id="396a3-210">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="396a3-211">Exemplo: "mostrar mais" e "mostrar armazenamento" pode ser um som muito semelhante.</span><span class="sxs-lookup"><span data-stu-id="396a3-211">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="396a3-212">**Cancele o registro do aplicativo quando não estiver em uso** - quando seu aplicativo não estiver em um estado em que um determinado comando de fala seja válido, considere cancelar seu registro para evitar a confusão com outros comandos.</span><span class="sxs-lookup"><span data-stu-id="396a3-212">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="396a3-213">**Teste com sotaques diferentes** - teste seu aplicativo com usuários que tenham sotaques diferentes.</span><span class="sxs-lookup"><span data-stu-id="396a3-213">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="396a3-214">**Mantenha a consistência nos comandos de voz** - se "Voltar" vai para a página anterior, mantenha esse comportamento em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="396a3-214">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="396a3-215">**Evite usar comandos do sistema** - os comandos de voz a seguir são reservados para o sistema.</span><span class="sxs-lookup"><span data-stu-id="396a3-215">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="396a3-216">Eles não devem ser usados pelos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="396a3-216">These should not be used by applications.</span></span>
   * <span data-ttu-id="396a3-217">"Ei, Cortana!"</span><span class="sxs-lookup"><span data-stu-id="396a3-217">"Hey Cortana"</span></span>
   * <span data-ttu-id="396a3-218">"Selecionar"</span><span class="sxs-lookup"><span data-stu-id="396a3-218">"Select"</span></span>
   * <span data-ttu-id="396a3-219">"Ir para o início"</span><span class="sxs-lookup"><span data-stu-id="396a3-219">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="396a3-220">Vantagens da entrada de voz</span><span class="sxs-lookup"><span data-stu-id="396a3-220">Advantages of voice input</span></span>

<span data-ttu-id="396a3-221">A entrada de voz é uma maneira natural de comunicarmos nossas intenções.</span><span class="sxs-lookup"><span data-stu-id="396a3-221">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="396a3-222">A voz é especialmente boa em **atravessamentos** de interface porque pode ajudar os usuários a percorrer várias etapas de uma interface (um usuário pode dizer "voltar" ao olhar para uma página da Web, em vez de ter que ir para cima e pressionar o botão voltar no aplicativo).</span><span class="sxs-lookup"><span data-stu-id="396a3-222">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="396a3-223">Esse pequeno tempo de salvamento tem um **efeito emocional** poderoso sobre a percepção do usuário da experiência e dá uma pequena quantia superpotência.</span><span class="sxs-lookup"><span data-stu-id="396a3-223">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="396a3-224">O uso da voz também é um método de entrada conveniente quando nossos braços estão ocupados ou quando estamos **executando várias tarefas ao mesmo tempo**.</span><span class="sxs-lookup"><span data-stu-id="396a3-224">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="396a3-225">Em dispositivos em que é difícil digitar um teclado, o **ditado de voz** pode ser uma maneira alternativa eficiente de inserir texto.</span><span class="sxs-lookup"><span data-stu-id="396a3-225">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="396a3-226">Por fim, em alguns casos, quando o **intervalo de precisão** para olhar e gesto é limitado, a voz pode ajudar a desambiguar a intenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="396a3-226">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="396a3-227">**Como o uso da voz pode beneficiar o usuário?**</span><span class="sxs-lookup"><span data-stu-id="396a3-227">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="396a3-228">Reduz o tempo - deve tornar o objetivo final mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="396a3-228">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="396a3-229">Minimiza o esforço - deve tornar as tarefas mais fluídas e simples.</span><span class="sxs-lookup"><span data-stu-id="396a3-229">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="396a3-230">Reduz a carga cognitiva - é intuitivo e fácil de lembrar e aprender.</span><span class="sxs-lookup"><span data-stu-id="396a3-230">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="396a3-231">É socialmente aceitável - deve estar de acordo com as normas sociais em termos de comportamento.</span><span class="sxs-lookup"><span data-stu-id="396a3-231">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="396a3-232">É rotineiro - a voz pode facilmente se tornar um comportamento habitual.</span><span class="sxs-lookup"><span data-stu-id="396a3-232">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="396a3-233">Desafios para entrada de voz</span><span class="sxs-lookup"><span data-stu-id="396a3-233">Challenges for voice input</span></span>

<span data-ttu-id="396a3-234">Embora a entrada de voz seja ótima para muitos aplicativos diferentes, ela também enfrenta vários desafios.</span><span class="sxs-lookup"><span data-stu-id="396a3-234">While voice input is great for a lot of different applications, it also faces several challenges.</span></span> <span data-ttu-id="396a3-235">Entender as vantagens e os desafios da entrada de voz permite que os desenvolvedores de aplicativos tomem decisões mais inteligentes sobre como e quando usar a entrada de voz e para criar uma ótima experiência para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="396a3-235">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="396a3-236">**Entrada de voz para controle de entrada contínuo** O controle refinado é um deles.</span><span class="sxs-lookup"><span data-stu-id="396a3-236">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="396a3-237">Por exemplo, um usuário pode querer alterar seu volume em seu aplicativo de música.</span><span class="sxs-lookup"><span data-stu-id="396a3-237">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="396a3-238">Ela pode simplesmente dizer "mais alto", mas não fica claro quanto mais alto o sistema deve fazer o volume.</span><span class="sxs-lookup"><span data-stu-id="396a3-238">She can simply say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="396a3-239">O usuário poderia dizer: "torná-lo um pouco mais alto", mas "um pouco" é difícil quantificar.</span><span class="sxs-lookup"><span data-stu-id="396a3-239">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="396a3-240">A movimentação ou o dimensionamento de hologramas com voz é difícil.</span><span class="sxs-lookup"><span data-stu-id="396a3-240">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="396a3-241">**Confiabilidade da detecção de entrada de voz** Embora os sistemas de entrada de voz se tornem melhores e melhores, às vezes eles podem ouvir e interpretar um comando de voz incorretamente.</span><span class="sxs-lookup"><span data-stu-id="396a3-241">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="396a3-242">A chave é resolver esse desafio em seu aplicativo fornecendo comentários ao usuário quando o sistema está escutando e o que o sistema entendeu para criar uma clareza sobre possíveis problemas no entendimento correto do usuário.</span><span class="sxs-lookup"><span data-stu-id="396a3-242">The key is to address this challenge in your application by providing feedback to the user when the system is listening and what the system understood to create clarity on potential issues in correctly understanding the user.</span></span>  

<span data-ttu-id="396a3-243">**Entrada de voz em espaços compartilhados** A voz pode não ser socialmente aceitável em espaços que você compartilha com outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="396a3-243">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="396a3-244">Veja aqui alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="396a3-244">Here are a few examples:</span></span>
* <span data-ttu-id="396a3-245">O usuário pode não querer perturbar outros (por exemplo, em uma biblioteca silenciosa ou em um escritório compartilhado)</span><span class="sxs-lookup"><span data-stu-id="396a3-245">The user may not want to disturb others (e.g., in a quiet library or shared office)</span></span>
* <span data-ttu-id="396a3-246">Os usuários podem se sentir inconvenientes sendo vistos por si mesmos em público,</span><span class="sxs-lookup"><span data-stu-id="396a3-246">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="396a3-247">Um usuário pode sentir-se desconfortável ditando uma mensagem pessoal ou confidencial (incluindo senhas) enquanto outras estão ouvindo</span><span class="sxs-lookup"><span data-stu-id="396a3-247">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="396a3-248">**Entrada de voz de palavras exclusivas ou desconhecidas** As dificuldades de entrada de voz também são fornecidas quando os usuários estão ditando palavras que podem ser desconhecidas do sistema, como apelidos, determinadas palavras gírias ou abreviações.</span><span class="sxs-lookup"><span data-stu-id="396a3-248">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words or abbreviations.</span></span> 

<span data-ttu-id="396a3-249">**Comandos de voz de aprendizagem** Embora o objetivo final seja conversar naturalmente com seu sistema, muitas vezes, os aplicativos ainda dependem de comandos de voz predefinidos específicos.</span><span class="sxs-lookup"><span data-stu-id="396a3-249">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often times apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="396a3-250">Um desafio associado a um grande conjunto de comandos de voz é como ensiná-los sem sobrecarregar o usuário e como ajudar o usuário a mantê-los.</span><span class="sxs-lookup"><span data-stu-id="396a3-250">A challenge associated with a big set of voice commands is how to teach them without overloading the user and how to help the user to retain them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="396a3-251">Estados de retorno de voz</span><span class="sxs-lookup"><span data-stu-id="396a3-251">Voice feedback states</span></span>

<span data-ttu-id="396a3-252">Quando a voz é aplicada corretamente, o usuário sabe **o que pode dizer e obtém um retorno claro**, e o sistema **o ouve corretamente**.</span><span class="sxs-lookup"><span data-stu-id="396a3-252">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="396a3-253">Esses dois sinais fazem o usuário se sentir seguro para usar a Voz como uma entrada primária.</span><span class="sxs-lookup"><span data-stu-id="396a3-253">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="396a3-254">A seguir, um diagrama mostrando o que acontece com o cursor quando a entrada de voz é reconhecida e como ele comunica isso ao usuário.</span><span class="sxs-lookup"><span data-stu-id="396a3-254">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="396a3-255">![1. Estado de cursor regular](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="396a3-255">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="396a3-256">**1. Estado regular do cursor**</span><span class="sxs-lookup"><span data-stu-id="396a3-256">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="396a3-257">![2. Comunica os comentários de voz e, em seguida, desaparece](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="396a3-257">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="396a3-258">**2. comunica os comentários de voz e, em seguida, desaparece**</span><span class="sxs-lookup"><span data-stu-id="396a3-258">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="396a3-259">![\* 3.</span><span class="sxs-lookup"><span data-stu-id="396a3-259">![\*3.</span></span> <span data-ttu-id="396a3-260">Estado de cursor regular](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="396a3-260">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="396a3-261">**3. retorna ao Estado regular do cursor**</span><span class="sxs-lookup"><span data-stu-id="396a3-261">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="396a3-262">As principais coisas que os usuários devem saber sobre "fala" na realidade misturada</span><span class="sxs-lookup"><span data-stu-id="396a3-262">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="396a3-263">Diga **"Selecionar"** ao focalizar um botão (você pode usar esse comando em qualquer lugar para clicar em um botão).</span><span class="sxs-lookup"><span data-stu-id="396a3-263">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="396a3-264">Você pode dizer o **nome do rótulo de um botão da barra de aplicativos** em alguns aplicativos para realizar uma ação.</span><span class="sxs-lookup"><span data-stu-id="396a3-264">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="396a3-265">Por exemplo, olhando para um aplicativo, um usuário pode dizer o comando "Remover" para remover o aplicativo do mundo (isso economiza tempo, pois você não precisa clicar nele com a mão).</span><span class="sxs-lookup"><span data-stu-id="396a3-265">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="396a3-266">Você pode iniciar a escuta da Cortana dizendo **"Ei, Cortana".**</span><span class="sxs-lookup"><span data-stu-id="396a3-266">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="396a3-267">Você pode fazer perguntas ("Ei, Cortana! Qual é a altura da Torre Eiffel?"), pedir para ela abrir um aplicativo ("Ei, Cortana! Abra o Netflix") ou pedir para ela abrir o Menu Iniciar ("Ei, Cortana! Abra o menu Iniciar") e muito mais.</span><span class="sxs-lookup"><span data-stu-id="396a3-267">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="396a3-268">Perguntas e preocupações comuns dos usuários em relação à voz</span><span class="sxs-lookup"><span data-stu-id="396a3-268">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="396a3-269">O que posso falar?</span><span class="sxs-lookup"><span data-stu-id="396a3-269">What can I say?</span></span>
* <span data-ttu-id="396a3-270">Como saberei que o sistema me ouviu corretamente?</span><span class="sxs-lookup"><span data-stu-id="396a3-270">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="396a3-271">O sistema não entende corretamente meus comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="396a3-271">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="396a3-272">Ele não reage quando dou um comando de voz.</span><span class="sxs-lookup"><span data-stu-id="396a3-272">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="396a3-273">Ele reage de maneira errada quando dou um comando de voz.</span><span class="sxs-lookup"><span data-stu-id="396a3-273">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="396a3-274">Como direcionar minha voz a um aplicativo específico ou a um comando de aplicativo?</span><span class="sxs-lookup"><span data-stu-id="396a3-274">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="396a3-275">Posso usar a voz para comandar as coisas no quadro holográfico do HoloLens?</span><span class="sxs-lookup"><span data-stu-id="396a3-275">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="396a3-276">Comunicação</span><span class="sxs-lookup"><span data-stu-id="396a3-276">Communication</span></span>

<span data-ttu-id="396a3-277">Para aplicativos que desejam aproveitar as opções de processamento de entrada de áudio personalizadas fornecidas pelo HoloLens, é importante entender as várias [categorias de fluxo de áudio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) que seu aplicativo pode consumir.</span><span class="sxs-lookup"><span data-stu-id="396a3-277">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="396a3-278">O Windows 10 dá suporte a várias categorias de fluxo diferentes e o HoloLens usa três delas para habilitar o processamento personalizado para otimizar a qualidade de áudio do microfone adaptada para fala, comunicação e outras que podem ser usadas para áudio de ambiente de ambientes cenários de captura (ou seja, "camcorder").</span><span class="sxs-lookup"><span data-stu-id="396a3-278">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="396a3-279">A categoria AudioCategory_Communications Stream é personalizada para cenários de qualidade de chamada e narração e fornece ao cliente um fluxo de áudio 16kHz 24bit mono da voz do usuário</span><span class="sxs-lookup"><span data-stu-id="396a3-279">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="396a3-280">A categoria AudioCategory_Speech Stream é personalizada para o mecanismo de fala do HoloLens (Windows) e fornece um fluxo 16kHz 24bit mono da voz do usuário.</span><span class="sxs-lookup"><span data-stu-id="396a3-280">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="396a3-281">Essa categoria pode ser usada por mecanismos de fala de terceiros, se necessário.</span><span class="sxs-lookup"><span data-stu-id="396a3-281">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="396a3-282">A categoria de AudioCategory_Other Stream é personalizada para a gravação de áudio do ambiente ambiental e fornece ao cliente um fluxo de áudio estéreo de 24 bits 48kHz.</span><span class="sxs-lookup"><span data-stu-id="396a3-282">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="396a3-283">Todo esse processamento de áudio é acelerado por hardware, o que significa que os recursos esgotam muito menos energia do que se o mesmo processamento foi feito na CPU do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="396a3-283">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="396a3-284">Evite executar outro processamento de entrada de áudio na CPU para maximizar a vida útil da bateria do sistema e aproveitar o processamento de entrada de áudio descarregado interno.</span><span class="sxs-lookup"><span data-stu-id="396a3-284">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="396a3-285">Idiomas</span><span class="sxs-lookup"><span data-stu-id="396a3-285">Languages</span></span>

<span data-ttu-id="396a3-286">O HoloLens 2 também dá suporte a idiomas adicionais.</span><span class="sxs-lookup"><span data-stu-id="396a3-286">HoloLens 2 also supports additional languages.</span></span> <span data-ttu-id="396a3-287">Tenha em mente que os comandos de fala sempre serão executados no idioma de exibição do sistema, mesmo se vários teclados estiverem instalados ou se os aplicativos tentarem criar um reconhecedor de fala em um idioma diferente.</span><span class="sxs-lookup"><span data-stu-id="396a3-287">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="396a3-288">Painel de controle da</span><span class="sxs-lookup"><span data-stu-id="396a3-288">Troubleshooting</span></span>

<span data-ttu-id="396a3-289">Se você tiver problemas ao usar "Select" e "Ei Cortana", tente mudar para um espaço mais silencioso, desativando a fonte de ruído ou falando mais alto.</span><span class="sxs-lookup"><span data-stu-id="396a3-289">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="396a3-290">Neste momento, todo o reconhecimento de fala no HoloLens é ajustado e otimizado especificamente para os palestrantes nativos do Estados Unidos Inglês.</span><span class="sxs-lookup"><span data-stu-id="396a3-290">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="396a3-291">Para o Windows Mixed Reality Developer Edition versão 2017, a lógica de gerenciamento de ponto de extremidade de áudio funcionará bem (para sempre) depois de fazer logoff e voltar para a área de trabalho do PC após a conexão inicial do HMD.</span><span class="sxs-lookup"><span data-stu-id="396a3-291">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="396a3-292">Antes do primeiro evento de saída/entrada depois de passar pelo WMR OOBE, o usuário poderia experimentar vários problemas de funcionalidade de áudio, variando de sem áudio para nenhuma alternância de áudio, dependendo de como o sistema foi configurado antes de conectar o HMD pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="396a3-292">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="396a3-293">Entrada de voz em MRTK (Kit de ferramentas de realidade misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="396a3-293">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="396a3-294">Com o **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , você pode atribuir facilmente o comando de voz em qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="396a3-294">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="396a3-295">Use o **perfil de entrada de fala** do MRTK para definir suas palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="396a3-295">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="396a3-296">Ao atribuir o script **SpeechInputHandler** , você pode fazer com que qualquer objeto responda às palavras-chave definidas no perfil de entrada de fala.</span><span class="sxs-lookup"><span data-stu-id="396a3-296">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="396a3-297">O SpeechInputHandler também fornece um rótulo de confirmação de fala para melhorar a confiança do usuário.</span><span class="sxs-lookup"><span data-stu-id="396a3-297">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="396a3-298">MRTK-comando de voz</span><span class="sxs-lookup"><span data-stu-id="396a3-298">MRTK - Voice command</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a><span data-ttu-id="396a3-299">Veja também</span><span class="sxs-lookup"><span data-stu-id="396a3-299">See also</span></span>
* [<span data-ttu-id="396a3-300">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="396a3-300">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="396a3-301">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="396a3-301">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="396a3-302">Entrada MR 212: voz</span><span class="sxs-lookup"><span data-stu-id="396a3-302">MR Input 212: Voice</span></span>](holograms-212.md)
* [<span data-ttu-id="396a3-303">Entrada de voz no DirectX</span><span class="sxs-lookup"><span data-stu-id="396a3-303">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="396a3-304">Entrada de voz no Unity</span><span class="sxs-lookup"><span data-stu-id="396a3-304">Voice input in Unity</span></span>](voice-input-in-unity.md)

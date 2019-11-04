---
title: Cursores
description: Um cursor ou indicador de seu vetor de direcionamento, fornece comentários contínuos para que o usuário entenda o que o HoloLens entende sobre suas intenções.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1º gen), HoloLens 2, realidade misturada, cursores, direcionamento, olhar, gestos
ms.openlocfilehash: ef011d8400de1e23db3d6fb4b0f2a853d787ae86
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435776"
---
# <a name="cursors"></a><span data-ttu-id="20e66-104">Cursores</span><span class="sxs-lookup"><span data-stu-id="20e66-104">Cursors</span></span>

<span data-ttu-id="20e66-105">Um cursor ou indicador de seu vetor de direcionamento atual, fornece comentários contínuos para que o usuário entenda onde o fone de ouvido acredita que o foco atual está nesse momento.</span><span class="sxs-lookup"><span data-stu-id="20e66-105">A cursor, or indicator of your current targeting vector, provides continuous feedback for the user to understand where the headset believes their current focus is at that time.</span></span> <span data-ttu-id="20e66-106">O cursor permite que o usuário entenda seu ponto de direcionamento atual e atue como feedback para indicar qual área, holograma ou ponto responderá à entrada.</span><span class="sxs-lookup"><span data-stu-id="20e66-106">The cursor allows the user to understand their current targeting point and acts as feedback to indicate what area, hologram, or point will respond to input.</span></span> <span data-ttu-id="20e66-107">É a representação digital de onde o dispositivo entende a atenção do usuário (embora isso possa não ser o mesmo que determinar qualquer coisa sobre suas intenções).</span><span class="sxs-lookup"><span data-stu-id="20e66-107">It is the digital representation of where the device understands the user's attention to be (though that may not be the same as determining anything about their intentions).</span></span>

<span data-ttu-id="20e66-108">Os comentários fornecidos pelo cursor oferecem aos usuários a capacidade de prever como o sistema responderá, usará esse sinal como comentários para comunicar melhor sua intenção ao dispositivo e, por fim, ser mais confiante em relação às suas interações.</span><span class="sxs-lookup"><span data-stu-id="20e66-108">The feedback provided by the cursor offers users the ability to anticipate how the system will respond, use that signal as feedback to better communicate their intention to the device, and ultimately be more confident about their interactions.</span></span>

<span data-ttu-id="20e66-109">Há três tipos de cursores: **Finger, Ray**e **Head-olhar**.</span><span class="sxs-lookup"><span data-stu-id="20e66-109">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="20e66-110">Esses cursores de apontação funcionam com modalidades de entrada diferentes nos headsets HoloLens, HoloLens 2 e imersiva.</span><span class="sxs-lookup"><span data-stu-id="20e66-110">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="20e66-111">Abaixo está a orientação sobre qual tipo de cursor usar para cada tipo de headset e modelo de interação.</span><span class="sxs-lookup"><span data-stu-id="20e66-111">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="20e66-112">No MRTK (Kit de ferramentas de realidade misturada), criamos módulos de cursores do tipo "arrastar e soltar" para ajudá-lo a criar a experiência correta.</span><span class="sxs-lookup"><span data-stu-id="20e66-112">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>


## <a name="device-support"></a><span data-ttu-id="20e66-113">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="20e66-113">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="20e66-114"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="20e66-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="20e66-115"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="20e66-115"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="20e66-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="20e66-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="20e66-117"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="20e66-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="20e66-118">Cursor do dedo</span><span class="sxs-lookup"><span data-stu-id="20e66-118">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="20e66-119">✔️</span><span class="sxs-lookup"><span data-stu-id="20e66-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="20e66-120">Cursor Ray</span><span class="sxs-lookup"><span data-stu-id="20e66-120">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="20e66-121">✔️</span><span class="sxs-lookup"><span data-stu-id="20e66-121">✔️</span></span></td>
        <td><span data-ttu-id="20e66-122">✔️</span><span class="sxs-lookup"><span data-stu-id="20e66-122">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="20e66-123">Cursor de olhar de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="20e66-123">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="20e66-124">✔️</span><span class="sxs-lookup"><span data-stu-id="20e66-124">✔️</span></span></td>
        <td><span data-ttu-id="20e66-125">✔️</span><span class="sxs-lookup"><span data-stu-id="20e66-125">✔️</span></span></td>
        <td><span data-ttu-id="20e66-126">✔️</span><span class="sxs-lookup"><span data-stu-id="20e66-126">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="20e66-127">Cursor do dedo</span><span class="sxs-lookup"><span data-stu-id="20e66-127">Finger cursor</span></span>
<span data-ttu-id="20e66-128">O cursor do dedo está disponível apenas no HoloLens 2 para aprimorar o modo de interação "[manipulação direta com mãos](direct-manipulation.md)".</span><span class="sxs-lookup"><span data-stu-id="20e66-128">The finger cursor is available only on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="20e66-129">Para entender melhor onde o dedo está apontando, anexamos anéis às dicas de ambos os dedos de índice.</span><span class="sxs-lookup"><span data-stu-id="20e66-129">To better understand where the finger is pointing, we have attached rings to the tips of both index fingers.</span></span> <span data-ttu-id="20e66-130">O tamanho do anel é baseado na proximidade do dedo com a superfície da interface do usuário (quanto mais próximo do dedo, menor o anel) e será reduzido para uma forma de ponto quando o dedo fizer contato com a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="20e66-130">The ring size is based on the proximity of the finger to the UI surface (the closer the finger, the smaller the ring) and will shrink to a dot shape when the finger makes contact with the UI.</span></span> <br>

<span data-ttu-id="20e66-131">![do cursor Finger](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="20e66-131">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="20e66-132">**Estados de comentários visuais do cursor 1 do dedo** : o anel é reduzido para um ponto.</span><span class="sxs-lookup"><span data-stu-id="20e66-132">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="20e66-133">2: o anel se alinha com a superfície.</span><span class="sxs-lookup"><span data-stu-id="20e66-133">2: The ring aligns with surface.</span></span> <span data-ttu-id="20e66-134">3: o anel é perpendicular ao vetor de dedo.</span><span class="sxs-lookup"><span data-stu-id="20e66-134">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="20e66-135">4: nenhum anel.</span><span class="sxs-lookup"><span data-stu-id="20e66-135">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="20e66-136">Cursor Ray</span><span class="sxs-lookup"><span data-stu-id="20e66-136">Ray cursor</span></span>
<span data-ttu-id="20e66-137">Os cursores de raio são anexados ao fim dos raios distantes para permitir a manipulação de objetos que estão fora de mãos.</span><span class="sxs-lookup"><span data-stu-id="20e66-137">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="20e66-138">Em headsets de imersão, os raios saem dos controladores de movimento e dos cursores de fim em ponto.</span><span class="sxs-lookup"><span data-stu-id="20e66-138">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="20e66-139">No HoloLens 2, aproveitamos o modelo mental desses raios do controlador de movimento e raios de mão projetadas que se originam de Palms e terminam em cursores em forma de anel que são consistentes com cursores de dedos usados na manipulação direta.</span><span class="sxs-lookup"><span data-stu-id="20e66-139">In HoloLens 2, we leverage the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="20e66-140">![o controlador de cursor Ray](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="20e66-140">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="20e66-141">**Ray cursores de controladores de movimento**</span><span class="sxs-lookup"><span data-stu-id="20e66-141">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="20e66-142">![Ray cursor](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="20e66-142">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="20e66-143">**Raios cursores de mãos**</span><span class="sxs-lookup"><span data-stu-id="20e66-143">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a><span data-ttu-id="20e66-144">Cursor de olhar de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="20e66-144">Head-gaze cursor</span></span>
<span data-ttu-id="20e66-145">O cursor Head-olhar é um ponto que é anexado ao final de um vetor Head-olhar invisível que usa a posição e a rotação do ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="20e66-145">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="20e66-146">Para executar ações, esse cursor apontando é emparelhado com várias entradas de confirmação, como toque de ar, comandos de voz, duração e pressionamento de botão.</span><span class="sxs-lookup"><span data-stu-id="20e66-146">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="20e66-147">No HoloLens 2, o Head-olhar é melhor emparelhado com qualquer entrada de confirmação que não seja o toque de ar, pois haverá um conflito de interação entre o toque de ar e raios de distância.</span><span class="sxs-lookup"><span data-stu-id="20e66-147">In HoloLens 2, head-gaze is best paired with any commit input that is not air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="20e66-148">![do cursor olhar Head](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="20e66-148">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="20e66-149">**Cursor de cabeçalho olhar com gesto de mão**</span><span class="sxs-lookup"><span data-stu-id="20e66-149">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="20e66-150">](images/head-gaze-cursor-voice.png) de voz do cursor olhar Head ![</span><span class="sxs-lookup"><span data-stu-id="20e66-150">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="20e66-151">**Cursor de cabeçalho olhar com comando de voz**</span><span class="sxs-lookup"><span data-stu-id="20e66-151">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a><span data-ttu-id="20e66-152">Recomendações de personalização do cursor</span><span class="sxs-lookup"><span data-stu-id="20e66-152">Cursor customization recommendations</span></span>
<span data-ttu-id="20e66-153">Se você quiser personalizar os comportamentos e as aparências dos comentários do cursor, veja algumas recomendações de design:</span><span class="sxs-lookup"><span data-stu-id="20e66-153">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="20e66-154">Escala do cursor</span><span class="sxs-lookup"><span data-stu-id="20e66-154">Cursor scale</span></span>
* <span data-ttu-id="20e66-155">O cursor não deve ser maior do que os destinos disponíveis, permitindo que os usuários interajam com facilidade e exibam o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="20e66-155">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="20e66-156">Dependendo da experiência que você criar, dimensionar o cursor à medida que o usuário procura também é uma consideração importante.</span><span class="sxs-lookup"><span data-stu-id="20e66-156">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="20e66-157">Por exemplo, à medida que o usuário fica mais distante em sua experiência, o cursor não deve se tornar muito pequeno, de modo que ele seja perdido.</span><span class="sxs-lookup"><span data-stu-id="20e66-157">For example, as the user looks further away in your experience, the cursor should not become too small such that it's lost.</span></span>
* <span data-ttu-id="20e66-158">Ao dimensionar o cursor, considere aplicar uma animação suave a ele, pois ele é dimensionado para dar a ele uma sensação orgânica.</span><span class="sxs-lookup"><span data-stu-id="20e66-158">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="20e66-159">Evite obstruir o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="20e66-159">Avoid obstructing content.</span></span> <span data-ttu-id="20e66-160">Os hologramas são o que torna a experiência fácil de memorizar e o cursor não deve ser retirado delas.</span><span class="sxs-lookup"><span data-stu-id="20e66-160">Holograms are what make the experience memorable and the cursor should not be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="20e66-161">Forma de cursor de direção</span><span class="sxs-lookup"><span data-stu-id="20e66-161">Directionless cursor shape</span></span>
* <span data-ttu-id="20e66-162">Embora não haja uma forma de cursor à direita, recomendamos que você use uma forma sem direção como uma Torus.</span><span class="sxs-lookup"><span data-stu-id="20e66-162">Although there is no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="20e66-163">Um cursor que aponta em alguma direção (por exemplo, um cursor de seta tradicional) pode confundir o usuário para sempre verificar dessa forma.</span><span class="sxs-lookup"><span data-stu-id="20e66-163">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="20e66-164">Uma exceção a isso é quando se usa o cursor para comunicar a instrução de interação ao usuário.</span><span class="sxs-lookup"><span data-stu-id="20e66-164">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="20e66-165">Por exemplo, ao dimensionar hologramas no sistema operacional de realidade misturada, o cursor inclui temporariamente setas que instruem o usuário sobre como mover sua mão para dimensionar o holograma.</span><span class="sxs-lookup"><span data-stu-id="20e66-165">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="20e66-166">Aparência</span><span class="sxs-lookup"><span data-stu-id="20e66-166">Look and feel</span></span>
* <span data-ttu-id="20e66-167">Um cursor com formato de rosca ou Torus funciona para muitos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="20e66-167">A donut or torus shaped cursor works for a lot of applications.</span></span>
* <span data-ttu-id="20e66-168">Escolha uma cor e forma que melhor represente a experiência que você está criando.</span><span class="sxs-lookup"><span data-stu-id="20e66-168">Pick a color and shape that best represents the experience you are creating.</span></span>
* <span data-ttu-id="20e66-169">Os cursores estão especialmente sujeitos à [separação de cores](hologram-stability.md#color-separation).</span><span class="sxs-lookup"><span data-stu-id="20e66-169">Cursors are especially prone to [color separation](hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="20e66-170">Um cursor pequeno com opacidade equilibrada mantém-o informativo sem a predominante da hierarquia visual.</span><span class="sxs-lookup"><span data-stu-id="20e66-170">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="20e66-171">Seja Cognizant de usar sombras ou destaques por trás do cursor, pois eles podem obstruir o conteúdo e distrair a tarefa em questão.</span><span class="sxs-lookup"><span data-stu-id="20e66-171">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="20e66-172">Os cursores devem alinhar e Hug as superfícies em seu aplicativo, isso dará ao usuário a sensação de que o sistema pode ver onde estão olhando, mas também que o sistema está ciente de seus arredores.</span><span class="sxs-lookup"><span data-stu-id="20e66-172">Cursors should align to and hug the surfaces in your app, this will give the user a feeling that the system can see where they are looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="20e66-173">Por exemplo, no sistema operacional misto de realidade, o cursor se alinha às superfícies do mundo do usuário, criando uma sensação de conscientização do mundo, mesmo quando o usuário não está olhando diretamente para um holograma.</span><span class="sxs-lookup"><span data-stu-id="20e66-173">For example, in the Mixed Reality OS, the cursor aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="20e66-174">O bloqueio magnético do cursor para um elemento interativo quando está dentro da proximidade pode ajudar a melhorar a confiança que o usuário irá interagir com esse elemento quando executar uma ação de seleção.</span><span class="sxs-lookup"><span data-stu-id="20e66-174">Magnetically locking the cursor to an interactive element when it is within close proximity can help improve confidence that user will interact with that element when they perform a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="20e66-175">Indicações visuais</span><span class="sxs-lookup"><span data-stu-id="20e66-175">Visual cues</span></span>
* <span data-ttu-id="20e66-176">Se sua experiência estiver concentrada em um único holograma, o cursor deverá alinhar e hugr apenas esse holograma e alterar a forma quando você olhar para fora desse holograma.</span><span class="sxs-lookup"><span data-stu-id="20e66-176">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="20e66-177">Isso pode transmitir ao usuário que o holograma é acionável e pode interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="20e66-177">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="20e66-178">Se seu aplicativo usar o mapeamento espacial, o cursor poderá ser alinhado e Hug cada superfície que vê.</span><span class="sxs-lookup"><span data-stu-id="20e66-178">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="20e66-179">Isso fornece comentários aos usuários que o HoloLens e seu aplicativo podem ver seu espaço.</span><span class="sxs-lookup"><span data-stu-id="20e66-179">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="20e66-180">Isso reforça o fato de que os hologramas são reais e em nosso mundo e ajudam a preencher a lacuna entre o real e o virtual.</span><span class="sxs-lookup"><span data-stu-id="20e66-180">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="20e66-181">Tenha uma ideia do que o cursor deve fazer quando não há hologramas ou superfícies na exibição.</span><span class="sxs-lookup"><span data-stu-id="20e66-181">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="20e66-182">Colocá-lo em uma distância predeterminada na frente do usuário é uma opção.</span><span class="sxs-lookup"><span data-stu-id="20e66-182">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="20e66-183">Ações possíveis</span><span class="sxs-lookup"><span data-stu-id="20e66-183">Possible actions</span></span>
* <span data-ttu-id="20e66-184">O cursor pode ser representado por ícones diferentes para transmitir possíveis ações que um holograma pode executar, como dimensionamento ou rotação.</span><span class="sxs-lookup"><span data-stu-id="20e66-184">The cursor can be represented by different icons to convey possible actions a hologram can perform, such as scaling or rotation.</span></span>
* <span data-ttu-id="20e66-185">Somente adicione informações extras sobre o cursor se isso significa algo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="20e66-185">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="20e66-186">Caso contrário, os usuários talvez não percebam as alterações de estado ou ficam confusos com o cursor.</span><span class="sxs-lookup"><span data-stu-id="20e66-186">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="20e66-187">Estado de entrada</span><span class="sxs-lookup"><span data-stu-id="20e66-187">Input state</span></span>
* <span data-ttu-id="20e66-188">Poderíamos usar o cursor para exibir o estado ou a intenção de entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="20e66-188">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="20e66-189">Por exemplo, podemos exibir um ícone informando ao usuário que o sistema vê seu estado de mão e que o aplicativo sabe que está pronto para agir.</span><span class="sxs-lookup"><span data-stu-id="20e66-189">For example, we could display an icon telling the user the system sees their hand state and that the application knows they are ready to take action.</span></span>
* <span data-ttu-id="20e66-190">Também poderíamos usar o cursor para mostrar aos usuários que os comandos de voz foram ouvidos pelo sistema por meio de uma Change de cor momentânea</span><span class="sxs-lookup"><span data-stu-id="20e66-190">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color chang</span></span>

* <span data-ttu-id="20e66-191">Os seguintes Estados de cursor podem ser implementados de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="20e66-191">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="20e66-192">Você pode implementar esses Estados diferentes modelando o cursor como um computador de estado.</span><span class="sxs-lookup"><span data-stu-id="20e66-192">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="20e66-193">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="20e66-193">For example:</span></span>
    * <span data-ttu-id="20e66-194">Estado ocioso é onde você mostra o cursor padrão.</span><span class="sxs-lookup"><span data-stu-id="20e66-194">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="20e66-195">Estado pronto é quando você detecta a mão do usuário na posição pronta.</span><span class="sxs-lookup"><span data-stu-id="20e66-195">Ready state is when you have detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="20e66-196">O estado de interação é quando o usuário está executando uma interação específica.</span><span class="sxs-lookup"><span data-stu-id="20e66-196">Interaction state is when the user is performing a particular interaction.</span></span>
    * <span data-ttu-id="20e66-197">O estado de ações possível ou o estado de foco é quando você transmite possíveis ações que podem ser executadas em um holograma.</span><span class="sxs-lookup"><span data-stu-id="20e66-197">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="20e66-198">Você também pode implementar esses Estados em uma maneira que permite que você possa exibir ativos de arte diferentes quando diferentes Estados forem detectados.</span><span class="sxs-lookup"><span data-stu-id="20e66-198">You could also implement these states in a skin-able manner such that you can display different art assets when different states are detected.</span></span>

<br>

---


## <a name="going-cursor-free"></a><span data-ttu-id="20e66-199">Indo "sem cursor"</span><span class="sxs-lookup"><span data-stu-id="20e66-199">Going "cursor-free"</span></span>
<span data-ttu-id="20e66-200">A criação sem um cursor é recomendada quando o sentido do imersão é um componente-chave de uma experiência e quando as interações de ponteiro (por meio de olhar e gesto) não exigem uma ótima precisão.</span><span class="sxs-lookup"><span data-stu-id="20e66-200">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) do not require great precision.</span></span> <span data-ttu-id="20e66-201">O sistema ainda deve atender às necessidades que normalmente são atendidas por um cursor, fornecendo aos usuários comentários contínuos sobre o entendimento do sistema de seu apontador e ajudando-os a comunicar com segurança suas intenções ao sistema.</span><span class="sxs-lookup"><span data-stu-id="20e66-201">The system must still meet the needs that are normally met by a cursor by providing users with continuous feedback on the system's understanding of their pointing and helping them to confidently communicate their intentions to the system.</span></span> <span data-ttu-id="20e66-202">Isso pode ser alcançado por meio de outras alterações de estado perceptível.</span><span class="sxs-lookup"><span data-stu-id="20e66-202">This may be achievable through other noticeable state changes.</span></span>

<br>

---


## <a name="see-also"></a><span data-ttu-id="20e66-203">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20e66-203">See also</span></span>
* [<span data-ttu-id="20e66-204">Gestos</span><span class="sxs-lookup"><span data-stu-id="20e66-204">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="20e66-205">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="20e66-205">Head-gaze and commit</span></span>](gaze-and-commit.md)

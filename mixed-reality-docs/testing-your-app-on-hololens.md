---
title: Testar seu aplicativo no HoloLens
description: Diretrizes e sugestões para testar um aplicativo HoloLens
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, testing
ms.openlocfilehash: 35e8eff230cdcd719952ad2633ec610c9a9a26a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59589567"
---
# <a name="testing-your-app-on-hololens"></a><span data-ttu-id="9bd91-104">Testar seu aplicativo no HoloLens</span><span class="sxs-lookup"><span data-stu-id="9bd91-104">Testing your app on HoloLens</span></span>

<span data-ttu-id="9bd91-105">Testar aplicativos HoloLens são muito semelhantes para testar aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="9bd91-105">Testing HoloLens applications are very similar to testing Windows applications.</span></span> <span data-ttu-id="9bd91-106">Todas as áreas comuns devem ser consideradas (funcionalidade, interoperabilidade, desempenho, segurança, confiabilidade, etc.).</span><span class="sxs-lookup"><span data-stu-id="9bd91-106">All the usual areas should be considered (functionality, interoperability, performance, security, reliability, etc.).</span></span> <span data-ttu-id="9bd91-107">No entanto, há algumas áreas que exigem tratamento especial ou atenção a detalhes que geralmente não são observadas em aplicativos de PC ou telefone.</span><span class="sxs-lookup"><span data-stu-id="9bd91-107">There are, however, some areas that require special handling or attention to details that are not usually observed in PC or phone apps.</span></span> <span data-ttu-id="9bd91-108">Aplicativos holográfico precisam executar sem problemas em um conjunto diversificado de ambientes.</span><span class="sxs-lookup"><span data-stu-id="9bd91-108">Holographic apps need to run smoothly in a diverse set of environments.</span></span> <span data-ttu-id="9bd91-109">Eles também precisam manter o conforto de desempenho e o usuário em todos os momentos.</span><span class="sxs-lookup"><span data-stu-id="9bd91-109">They also need to maintain performance and user comfort at all times.</span></span> <span data-ttu-id="9bd91-110">Diretrizes para essas áreas de teste é detalhada neste tópico.</span><span class="sxs-lookup"><span data-stu-id="9bd91-110">Guidance for testing these areas is detailed in this topic.</span></span>

## <a name="performance"></a><span data-ttu-id="9bd91-111">Desempenho</span><span class="sxs-lookup"><span data-stu-id="9bd91-111">Performance</span></span>

<span data-ttu-id="9bd91-112">Aplicativos holográfico precisam executar sem problemas em um conjunto diversificado de ambientes.</span><span class="sxs-lookup"><span data-stu-id="9bd91-112">Holographic apps need to run smoothly in a diverse set of environments.</span></span> <span data-ttu-id="9bd91-113">Eles também precisam manter o conforto de desempenho e o usuário em todos os momentos.</span><span class="sxs-lookup"><span data-stu-id="9bd91-113">They also need to maintain performance and user comfort at all times.</span></span> <span data-ttu-id="9bd91-114">Desempenho é tão importante para a experiência do usuário com um aplicativo holográfica que temos um tópico inteiro dedicado a ele.</span><span class="sxs-lookup"><span data-stu-id="9bd91-114">Performance is so important to the user's experience with a Holographic app that we have an entire topic devoted to it.</span></span> <span data-ttu-id="9bd91-115">Certifique-se de que você leia e siga o [Noções básicas sobre desempenho para realidade misturada](understanding-performance-for-mixed-reality.md)</span><span class="sxs-lookup"><span data-stu-id="9bd91-115">Please make sure you read and follow the [Understanding Performance for Mixed Reality](understanding-performance-for-mixed-reality.md)</span></span>

## <a name="testing-3d-in-3d"></a><span data-ttu-id="9bd91-116">Teste 3D em 3D</span><span class="sxs-lookup"><span data-stu-id="9bd91-116">Testing 3D in 3D</span></span>
1. <span data-ttu-id="9bd91-117">**Teste seu aplicativo em diferentes espaços tantos quanto possível.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-117">**Test your app in as many different spaces as possible.**</span></span> <span data-ttu-id="9bd91-118">Tente em salas de big, salas de pequenas, banheiros, cozinhas, quartos, escritórios, etc. Também leva em salas de consideração com recursos fora do padrão como paredes não verticais, curvas paredes, tetos não horizontais.</span><span class="sxs-lookup"><span data-stu-id="9bd91-118">Try in big rooms, small rooms, bathrooms, kitchens, bedrooms, offices, etc. Also take into consideration rooms with non standard features such as non vertical walls, curved walls, non-horizontal ceilings.</span></span> <span data-ttu-id="9bd91-119">Ele funciona bem quando a transição entre os ambientes, andares, percorrer os corredores ou escadas?</span><span class="sxs-lookup"><span data-stu-id="9bd91-119">Does it work well when transitioning between rooms, floors, going through hallways or stairs?</span></span>
2. <span data-ttu-id="9bd91-120">**Teste seu aplicativo em condições de iluminação diferentes.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-120">**Test your app in different lighting conditions.**</span></span> <span data-ttu-id="9bd91-121">Ele responde corretamente para diferentes condições ambientais, como iluminação, pretas superfícies, transparente refletiva superfícies como espelhos, paredes de vidro, etc.</span><span class="sxs-lookup"><span data-stu-id="9bd91-121">Does it respond properly to different environmental conditions such as lighting, black surfaces, transparent/reflective surfaces such as mirrors, glass walls, etc.</span></span>
3. <span data-ttu-id="9bd91-122">**Teste seu aplicativo em condições diferentes de movimento.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-122">**Test your app in different motion conditions.**</span></span> <span data-ttu-id="9bd91-123">Coloque no dispositivo e tente a seus cenários em vários estados de movimento.</span><span class="sxs-lookup"><span data-stu-id="9bd91-123">Put on device and try your scenarios in various states of motion.</span></span> <span data-ttu-id="9bd91-124">Ele responde corretamente para movimentação diferente ou em estado estável?</span><span class="sxs-lookup"><span data-stu-id="9bd91-124">Does it respond properly to different movement or steady state?</span></span>
4. <span data-ttu-id="9bd91-125">**Teste o funcionamento do seu aplicativo de ângulos diferentes.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-125">**Test how your app works from different angles.**</span></span> <span data-ttu-id="9bd91-126">Se você tiver um holograma mundo bloqueado, o que acontece se o usuário o conduz por trás dele?</span><span class="sxs-lookup"><span data-stu-id="9bd91-126">If you have a world locked hologram, what happens if your user walks behind it?</span></span> <span data-ttu-id="9bd91-127">O que acontece se trata de algo entre o usuário e o holograma?</span><span class="sxs-lookup"><span data-stu-id="9bd91-127">What happens if something comes between the user and the hologram?</span></span> <span data-ttu-id="9bd91-128">E se o usuário examina o holograma acima ou abaixo?</span><span class="sxs-lookup"><span data-stu-id="9bd91-128">What if the user looks at the hologram from above or below?</span></span>
5. <span data-ttu-id="9bd91-129">**Use as indicações de áudio e espaciais.** Verifique se que seu aplicativo utiliza para impedir que o usuário se percam.</span><span class="sxs-lookup"><span data-stu-id="9bd91-129">**Use spatial and audio cues.** Make sure your app uses these to prevent the user from getting lost.</span></span>
6. <span data-ttu-id="9bd91-130">**Teste seu aplicativo em diferentes níveis de ruído do ambiente.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-130">**Test your app at different levels of ambient noise.**</span></span> <span data-ttu-id="9bd91-131">Se você já implementou comandos de voz, tente invocá-las com níveis variados de ruído do ambiente.</span><span class="sxs-lookup"><span data-stu-id="9bd91-131">If you've implemented voice commands, try invoking them with varying levels of ambient noise.</span></span>
7. <span data-ttu-id="9bd91-132">**Testar seu aplicativo encaixado e permanente**.</span><span class="sxs-lookup"><span data-stu-id="9bd91-132">**Test your app seated and standing**.</span></span> <span data-ttu-id="9bd91-133">Certifique-se de testar de assentos e posições de pé.</span><span class="sxs-lookup"><span data-stu-id="9bd91-133">Make sure to test from both seating and standing positions.</span></span>
8. <span data-ttu-id="9bd91-134">**Teste seu aplicativo de distâncias diferentes**.</span><span class="sxs-lookup"><span data-stu-id="9bd91-134">**Test your app from different distances**.</span></span> <span data-ttu-id="9bd91-135">Elementos de interface do usuário podem ser lidos e interagidos de longe?</span><span class="sxs-lookup"><span data-stu-id="9bd91-135">Can UI elements be read and interacted with from far away?</span></span> <span data-ttu-id="9bd91-136">Faz o react seu aplicativo para que os usuários recebam muito perto de seu hologramas?</span><span class="sxs-lookup"><span data-stu-id="9bd91-136">Does your app react to users getting too close to your holograms?</span></span>
9. <span data-ttu-id="9bd91-137">**Teste seu aplicativo em relação a interações de barra de aplicativo comuns**.</span><span class="sxs-lookup"><span data-stu-id="9bd91-137">**Test your app against common app bar interactions**.</span></span> <span data-ttu-id="9bd91-138">Todos os blocos de aplicativos e aplicativos universais 2D têm uma [barra de aplicativo](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) que permite que você controle como o aplicativo é posicionado no mundo misto.</span><span class="sxs-lookup"><span data-stu-id="9bd91-138">All app tiles and 2D universal apps have a [app bar](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) that allows you to control how the app is positioned in the Mixed World.</span></span> <span data-ttu-id="9bd91-139">Certifique-se de clicar em Remover encerra o processo de aplicativo normalmente e que o botão Voltar é suportado dentro do contexto de seu aplicativo universal 2D.</span><span class="sxs-lookup"><span data-stu-id="9bd91-139">Make sure clicking Remove terminates your app process gracefully and that the Back button is supported within the context of your 2D universal app.</span></span> <span data-ttu-id="9bd91-140">Tente escalar e movendo seu aplicativo no [modo de ajuste](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) enquanto ele estiver ativo, e enquanto ele é um bloco de aplicativo suspenso.</span><span class="sxs-lookup"><span data-stu-id="9bd91-140">Try scaling and moving your app in [Adjust mode](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) both while it is active, and while it is a suspended app tile.</span></span>

### <a name="environmental-test-matrix"></a><span data-ttu-id="9bd91-141">Matriz de teste ambiental</span><span class="sxs-lookup"><span data-stu-id="9bd91-141">Environmental Test Matrix</span></span>

![Matriz de teste do ambiente para desenvolvimento de aplicativos do HoloLens](images/environment-matrix-600px.png)

## <a name="comfort"></a><span data-ttu-id="9bd91-143">Conforto</span><span class="sxs-lookup"><span data-stu-id="9bd91-143">Comfort</span></span>
1. <span data-ttu-id="9bd91-144">**Planos de recorte.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-144">**Clip planes.**</span></span> <span data-ttu-id="9bd91-145">Ser cuidadosa para onde [hologramas são renderizadas](hologram-stability.md#hologram-render-distances).</span><span class="sxs-lookup"><span data-stu-id="9bd91-145">Be attentive to where [holograms are rendered](hologram-stability.md#hologram-render-distances).</span></span>
2. <span data-ttu-id="9bd91-146">**Evite a movimentação de virtual inconsistente com a movimentação do cabeçote real.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-146">**Avoid virtual movement inconsistent with actual head movement.**</span></span> <span data-ttu-id="9bd91-147">Evite mover a câmera de forma que não é representativo do movimento de real do usuário.</span><span class="sxs-lookup"><span data-stu-id="9bd91-147">Avoid moving the camera in a way that is not representative of the user's actual motion.</span></span> <span data-ttu-id="9bd91-148">Se seu aplicativo precisar mover o usuário por meio de uma cena, tornar o movimento previsível, minimizar a aceleração e permitem que o usuário controle a movimentação.</span><span class="sxs-lookup"><span data-stu-id="9bd91-148">If your app requires moving the user through a scene, make the motion predictable, minimize acceleration, and let the user control the movement.</span></span>
3. <span data-ttu-id="9bd91-149">**Siga as diretrizes de qualidade holograma.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-149">**Follow the hologram quality guidelines.**</span></span> <span data-ttu-id="9bd91-150">Aplicativos de alto desempenho que implementam o [diretrizes de qualidade holograma](hologram-stability.md) têm menor probabilidade de resultar em discomfort do usuário.</span><span class="sxs-lookup"><span data-stu-id="9bd91-150">Performant apps that implement the [hologram quality guidance](hologram-stability.md) are less likely to result in user discomfort.</span></span>
4. <span data-ttu-id="9bd91-151">**Distribua hologramas horizontalmente em vez de verticalmente.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-151">**Distribute holograms horizontally rather than vertically.**</span></span> <span data-ttu-id="9bd91-152">Forçar o usuário gastar longos períodos de tempo procurando por ou para baixo, pode levar a fadiga no pescoço.</span><span class="sxs-lookup"><span data-stu-id="9bd91-152">Forcing the user to spend extended periods of time looking up or down can lead to fatigue in the neck.</span></span>

## <a name="input"></a><span data-ttu-id="9bd91-153">Entrada</span><span class="sxs-lookup"><span data-stu-id="9bd91-153">Input</span></span>

### <a name="gaze-and-gestures"></a><span data-ttu-id="9bd91-154">Olhar e gestos</span><span class="sxs-lookup"><span data-stu-id="9bd91-154">Gaze and Gestures</span></span>

<span data-ttu-id="9bd91-155">[Mantenha o foco](gaze.md) é um formulário básico de entrada em HoloLens que permitem que os usuários têm por objetivo hologramas e o ambiente.</span><span class="sxs-lookup"><span data-stu-id="9bd91-155">[Gaze](gaze.md) is a basic form of input on HoloLens that enable users to aim at holograms and the environment.</span></span> <span data-ttu-id="9bd91-156">Você pode visualmente ver onde seu foco está definindo como destino com base na posição do cursor.</span><span class="sxs-lookup"><span data-stu-id="9bd91-156">You can visually see where your gaze is targeting based on the cursor position.</span></span> <span data-ttu-id="9bd91-157">É comum para associar o cursor de olhar um cursor do mouse.</span><span class="sxs-lookup"><span data-stu-id="9bd91-157">It's common to associate the gaze cursor with a mouse cursor.</span></span>

<span data-ttu-id="9bd91-158">[Gestos](gestures.md) servem para interagir com hologramas, como um clique do mouse.</span><span class="sxs-lookup"><span data-stu-id="9bd91-158">[Gestures](gestures.md) are how you interact with holograms, like a mouse click.</span></span> <span data-ttu-id="9bd91-159">Na maioria das vezes os comportamentos de mouse e toque são os mesmos, mas é importante entender e validar quando eles forem diferentes.</span><span class="sxs-lookup"><span data-stu-id="9bd91-159">Most of the time the mouse and touch behaviors are the same, but it's important to understand and validate when they differ.</span></span>

<span data-ttu-id="9bd91-160">**Valide quando seu aplicativo tem um comportamento diferente com o mouse e toque.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-160">**Validate when your app has a different behavior with mouse and touch.**</span></span> <span data-ttu-id="9bd91-161">Isso será identificar inconsistências e ajudar a decisões de design para tornar a experiência mais natural para os usuários.</span><span class="sxs-lookup"><span data-stu-id="9bd91-161">This will identify inconsistencies and help with design decisions to make the experience more natural for users.</span></span> <span data-ttu-id="9bd91-162">Por exemplo, disparar uma ação com base em foco.</span><span class="sxs-lookup"><span data-stu-id="9bd91-162">For example, triggering an action based on hover.</span></span>

> [!NOTE]
> <span data-ttu-id="9bd91-163">Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="9bd91-163">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

### <a name="custom-voice-commands"></a><span data-ttu-id="9bd91-164">Comandos de voz personalizadas</span><span class="sxs-lookup"><span data-stu-id="9bd91-164">Custom Voice Commands</span></span>

<span data-ttu-id="9bd91-165">[Entrada de voz](voice-input.md) é uma forma natural de interação.</span><span class="sxs-lookup"><span data-stu-id="9bd91-165">[Voice input](voice-input.md) is a natural form of interaction.</span></span> <span data-ttu-id="9bd91-166">A experiência do usuário pode ser mágica ou confuso dependendo de sua escolha de comandos e como expô-los.</span><span class="sxs-lookup"><span data-stu-id="9bd91-166">The user experience can be magical or confusing depending on your choice of commands and how you expose them.</span></span> <span data-ttu-id="9bd91-167">Como regra, você não deve usar comandos de voz do sistema, como "Select" ou "Ei Cortana" como comandos personalizados.</span><span class="sxs-lookup"><span data-stu-id="9bd91-167">As a rule, you should not use system voice commands such as "Select" or "Hey Cortana" as custom commands.</span></span> <span data-ttu-id="9bd91-168">Aqui estão alguns pontos a serem considerados:</span><span class="sxs-lookup"><span data-stu-id="9bd91-168">Here are a few points to consider:</span></span>
1. <span data-ttu-id="9bd91-169">**Evite usar comandos que soam parecidos.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-169">**Avoid using commands that sound similar.**</span></span> <span data-ttu-id="9bd91-170">Potencialmente, isso pode disparar o comando incorreto.</span><span class="sxs-lookup"><span data-stu-id="9bd91-170">This can potentially trigger the incorrect command.</span></span>
2. <span data-ttu-id="9bd91-171">**Escolha palavras foneticamente avançadas quando possível.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-171">**Choose phonetically rich words when possible.**</span></span> <span data-ttu-id="9bd91-172">Isso irá minimizar e/ou evitar ativações falsos.</span><span class="sxs-lookup"><span data-stu-id="9bd91-172">This will minimize and/or avoid false activations.</span></span>

### <a name="peripherals"></a><span data-ttu-id="9bd91-173">Periféricos</span><span class="sxs-lookup"><span data-stu-id="9bd91-173">Peripherals</span></span>

<span data-ttu-id="9bd91-174">Os usuários podem interagir com seu aplicativo por meio [periféricos](hardware-accessories.md).</span><span class="sxs-lookup"><span data-stu-id="9bd91-174">Users can interact with your App through [peripherals](hardware-accessories.md).</span></span> <span data-ttu-id="9bd91-175">Aplicativos não precisam fazer nada especial para tirar proveito desse recurso, no entanto, há algumas coisas que vale a pena verificar.</span><span class="sxs-lookup"><span data-stu-id="9bd91-175">Apps don't need to do anything special to take advantage of that capability, however there are a couple things worth checking.</span></span>
1. <span data-ttu-id="9bd91-176">**Valide interações personalizadas.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-176">**Validate custom interactions.**</span></span> <span data-ttu-id="9bd91-177">Coisas como atalhos de teclado personalizados para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9bd91-177">Things like custom keyboard shortcuts for your app.</span></span>
2. <span data-ttu-id="9bd91-178">**Valide a alternância de tipos de entrada.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-178">**Validate switching input types.**</span></span> <span data-ttu-id="9bd91-179">Tentativa de usar vários métodos de entrada para concluir uma tarefa, como o gesto, voz, mouse e teclado tudo no mesmo cenário.</span><span class="sxs-lookup"><span data-stu-id="9bd91-179">Attempting to use multiple input methods to complete a task, such as voice, gesture, mouse, and keyboard all in the same scenario.</span></span>

## <a name="system-integration"></a><span data-ttu-id="9bd91-180">Integração do sistema</span><span class="sxs-lookup"><span data-stu-id="9bd91-180">System Integration</span></span>

### <a name="battery"></a><span data-ttu-id="9bd91-181">Bateria</span><span class="sxs-lookup"><span data-stu-id="9bd91-181">Battery</span></span>

<span data-ttu-id="9bd91-182">Teste seu aplicativo sem uma fonte de alimentação conectada para entender a rapidez ele descarrega a bateria.</span><span class="sxs-lookup"><span data-stu-id="9bd91-182">Test your application without a power source connected to understand how quickly it drains the battery.</span></span> <span data-ttu-id="9bd91-183">Um possa compreender facilmente o estado da bateria, observando as leituras do LED de energia.</span><span class="sxs-lookup"><span data-stu-id="9bd91-183">One can easily understand the battery state by looking at Power LED readings.</span></span> ![Estados de LED que indicam a energia da bateria](images/batterypowerledindication-500px.png)

### <a name="power-state-transitions"></a><span data-ttu-id="9bd91-185">Transições de estado de energia</span><span class="sxs-lookup"><span data-stu-id="9bd91-185">Power State Transitions</span></span>

<span data-ttu-id="9bd91-186">Valide o trabalho de cenários-chave conforme o esperado durante a transição entre estados de energia.</span><span class="sxs-lookup"><span data-stu-id="9bd91-186">Validate key scenarios work as expected when transitioning between power states.</span></span> <span data-ttu-id="9bd91-187">Por exemplo, o aplicativo permanece na sua posição original?</span><span class="sxs-lookup"><span data-stu-id="9bd91-187">For example, does the application remain at its original position?</span></span> <span data-ttu-id="9bd91-188">Ele manter corretamente seu estado?</span><span class="sxs-lookup"><span data-stu-id="9bd91-188">Does it correctly persist its state?</span></span> <span data-ttu-id="9bd91-189">Ele continua a funcionar conforme o esperado?</span><span class="sxs-lookup"><span data-stu-id="9bd91-189">Does it continue to function as expected?</span></span>
1. <span data-ttu-id="9bd91-190">**Espera / retomar.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-190">**Stand-by / Resume.**</span></span> <span data-ttu-id="9bd91-191">Para entrar no modo de espera, é possível pressionar e liberar o botão de energia imediatamente.</span><span class="sxs-lookup"><span data-stu-id="9bd91-191">To enter standby, one can press and release the power button immediately.</span></span> <span data-ttu-id="9bd91-192">Ele também entrará em espera automaticamente após três minutos de inatividade.</span><span class="sxs-lookup"><span data-stu-id="9bd91-192">The device also will enter standby automatically after 3 minutes of inactivity.</span></span> <span data-ttu-id="9bd91-193">Para retomar do modo de espera, é possível pressione e solte o botão de energia imediatamente.</span><span class="sxs-lookup"><span data-stu-id="9bd91-193">To resume from standby, one can press and release the power button immediately.</span></span> <span data-ttu-id="9bd91-194">O dispositivo também será retomada se você se conectar ou desconectar-se de uma fonte de energia.</span><span class="sxs-lookup"><span data-stu-id="9bd91-194">The device will also resume if you connect or disconnect it from a power source.</span></span>
2. <span data-ttu-id="9bd91-195">**Desligamento / reinício.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-195">**Shutdown / Restart.**</span></span> <span data-ttu-id="9bd91-196">Para desligar, pressione e segure o botão de energia continuamente para 6 segundos.</span><span class="sxs-lookup"><span data-stu-id="9bd91-196">To shutdown, press and hold the power button continuously for 6 seconds.</span></span> <span data-ttu-id="9bd91-197">Para reiniciar, pressione o botão de energia.</span><span class="sxs-lookup"><span data-stu-id="9bd91-197">To restart, press the power button.</span></span>

### <a name="multi-app-scenarios"></a><span data-ttu-id="9bd91-198">Cenários de vários aplicativos</span><span class="sxs-lookup"><span data-stu-id="9bd91-198">Multi-App Scenarios</span></span>

<span data-ttu-id="9bd91-199">Valide principal funcionalidade do aplicativo ao alternar entre aplicativos, especialmente se você já implementou uma tarefa em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="9bd91-199">Validate core app functionality when switching between apps, especially if you've implemented a background task.</span></span> <span data-ttu-id="9bd91-200">Copiar/colar e integração com o Cortana também são vale a pena verificar onde aplicável.</span><span class="sxs-lookup"><span data-stu-id="9bd91-200">Copy/Paste and Cortana integration are also worth checking where applicable.</span></span>

## <a name="telemetry"></a><span data-ttu-id="9bd91-201">Telemetria</span><span class="sxs-lookup"><span data-stu-id="9bd91-201">Telemetry</span></span>

<span data-ttu-id="9bd91-202">Usar telemetria e análise para orientá-lo.</span><span class="sxs-lookup"><span data-stu-id="9bd91-202">Use telemetry and analytics to guide you.</span></span> <span data-ttu-id="9bd91-203">Integração de análise em seu aplicativo ajudará você a obter insights sobre seu aplicativo de seus testadores Beta e usuários finais.</span><span class="sxs-lookup"><span data-stu-id="9bd91-203">Integrating analytics into your app will help you get insights about your app from your Beta testers and end-users.</span></span> <span data-ttu-id="9bd91-204">Esses dados podem ser usados para ajudar a otimizar seu aplicativo antes do envio para a Store e para atualizações futuras.</span><span class="sxs-lookup"><span data-stu-id="9bd91-204">This data can be used to help optimize your app before submission to the Store and for future updates.</span></span> <span data-ttu-id="9bd91-205">Há muitas opções de análise por aí.</span><span class="sxs-lookup"><span data-stu-id="9bd91-205">There are many analytics options out there.</span></span> <span data-ttu-id="9bd91-206">Se você não tiver certeza de onde começar, confira [App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx).</span><span class="sxs-lookup"><span data-stu-id="9bd91-206">If you're not sure where to start, check out [App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx).</span></span>

<span data-ttu-id="9bd91-207">Perguntas a serem consideradas:</span><span class="sxs-lookup"><span data-stu-id="9bd91-207">Questions to consider:</span></span>
1. <span data-ttu-id="9bd91-208">Como os usuários estão usando o espaço?</span><span class="sxs-lookup"><span data-stu-id="9bd91-208">How are users using the space?</span></span>
2. <span data-ttu-id="9bd91-209">O aplicativo é como colocar objetos do mundo - é possível detectar problemas?</span><span class="sxs-lookup"><span data-stu-id="9bd91-209">How is the app placing objects in the world - can you detect problems?</span></span>
3. <span data-ttu-id="9bd91-210">Quanto tempo eles gastam em diferentes estágios do aplicativo?</span><span class="sxs-lookup"><span data-stu-id="9bd91-210">How much time do they spend on different stages of the application?</span></span>
4. <span data-ttu-id="9bd91-211">Quanto tempo eles gastam no aplicativo?</span><span class="sxs-lookup"><span data-stu-id="9bd91-211">How much time do they spend in the app?</span></span>
5. <span data-ttu-id="9bd91-212">Quais são os caminhos de uso mais comuns, os usuários está tentando?</span><span class="sxs-lookup"><span data-stu-id="9bd91-212">What are the most common usage paths the users are trying?</span></span>
6. <span data-ttu-id="9bd91-213">Os usuários estão atingindo estados inesperados e/ou erros?</span><span class="sxs-lookup"><span data-stu-id="9bd91-213">Are users hitting unexpected states and/or errors?</span></span>

## <a name="emulator-and-simulated-input"></a><span data-ttu-id="9bd91-214">Emulador e entrada simulada</span><span class="sxs-lookup"><span data-stu-id="9bd91-214">Emulator and Simulated Input</span></span>

<span data-ttu-id="9bd91-215">O [HoloLens emulador](using-the-hololens-emulator.md) é uma ótima maneira de testar com eficiência o seu aplicativo holográfico com uma variedade de características do usuário simulado e espaços.</span><span class="sxs-lookup"><span data-stu-id="9bd91-215">The [HoloLens emulator](using-the-hololens-emulator.md) is a great way to efficiently test your Holographic app with a variety of simulated user characteristics and spaces.</span></span> <span data-ttu-id="9bd91-216">Aqui estão algumas sugestões para usar efetivamente o emulador para testar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="9bd91-216">Here are some suggestions for effectively using the emulator to test your app:</span></span>
1. <span data-ttu-id="9bd91-217">**Use os ambientes virtuais do emulador para expandir seu teste.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-217">**Use the emulator's virtual rooms to expand your testing.**</span></span> <span data-ttu-id="9bd91-218">O emulador vem com um conjunto de ambientes virtuais que você pode usar para testar seu aplicativo em ambientes ainda mais.</span><span class="sxs-lookup"><span data-stu-id="9bd91-218">The emulator comes with a set of virtual rooms that you can use to test your app in even more environments.</span></span>
2. <span data-ttu-id="9bd91-219">**Use o emulador para examinar seu aplicativo de todos os ângulos.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-219">**Use the emulator to look at your app from all angles.**</span></span> <span data-ttu-id="9bd91-220">As chaves PageUp/Pagabaixo tornará seu simulada do usuário mais alta ou mais curta.</span><span class="sxs-lookup"><span data-stu-id="9bd91-220">The PageUp/PageDn keys will make your simulated user taller or shorter.</span></span>
3. <span data-ttu-id="9bd91-221">**Teste seu aplicativo com um HoloLens real.**</span><span class="sxs-lookup"><span data-stu-id="9bd91-221">**Test your app with a real HoloLens.**</span></span> <span data-ttu-id="9bd91-222">O emulador do HoloLens é uma excelente ferramenta para ajudá-lo rapidamente iterar em um aplicativo e detectar os bugs novos, mas certifique-se de também testar em um HoloLens físico antes de enviar para a Windows Store.</span><span class="sxs-lookup"><span data-stu-id="9bd91-222">The HoloLens Emulator is a great tool to help you quickly iterate on an app and catch new bugs, but make sure you also test on a physical HoloLens before submitting to the Windows Store.</span></span> <span data-ttu-id="9bd91-223">Isso é importante para garantir que o desempenho e a experiência sejam ótimos no hardware real.</span><span class="sxs-lookup"><span data-stu-id="9bd91-223">This is important to ensure that the performance and experience are great on real hardware.</span></span>

## <a name="automated-testing-with-perception-simulation"></a><span data-ttu-id="9bd91-224">Testes automatizados com percepção de simulação</span><span class="sxs-lookup"><span data-stu-id="9bd91-224">Automated testing with Perception Simulation</span></span>

<span data-ttu-id="9bd91-225">Alguns desenvolvedores de aplicativo talvez queira automatizar os testes de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9bd91-225">Some app developers might want to automate testing of their apps.</span></span> <span data-ttu-id="9bd91-226">Além dos testes de unidade simples, você pode usar o [simulação de percepção](perception-simulation.md) pilha no HoloLens, automatizar entrada humana e mundiais para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9bd91-226">Beyond simple unit tests, you can use the [perception simulation](perception-simulation.md) stack in HoloLens to automate human and world input to your app.</span></span> <span data-ttu-id="9bd91-227">A API de simulação de percepção pode enviar entrada simulada para o emulador do HoloLens ou um HoloLens físico.</span><span class="sxs-lookup"><span data-stu-id="9bd91-227">The perception simulation API can send simulated input to either the HoloLens emulator or a physical HoloLens.</span></span>

## <a name="windows-app-certification-kit"></a><span data-ttu-id="9bd91-228">Kit de Certificação de Aplicativos Windows</span><span class="sxs-lookup"><span data-stu-id="9bd91-228">Windows App Certification Kit</span></span>

<span data-ttu-id="9bd91-229">Para dar ao seu aplicativo a melhor chance de que está sendo [publicadas na Windows Store](submitting-an-app-to-the-microsoft-store.md), validar e testá-lo localmente antes de enviá-lo para certificação.</span><span class="sxs-lookup"><span data-stu-id="9bd91-229">To give your app the best chance of being [published on the Windows Store](submitting-an-app-to-the-microsoft-store.md), validate and test it locally before you submit it for certification.</span></span> <span data-ttu-id="9bd91-230">Se seu aplicativo for destinado a família do dispositivo Windows.Holographic, o [Kit de certificação de aplicativos do Windows](https://msdn.microsoft.com/library/windows/apps/xaml/mt186449.aspx) só executará testes de análise estática de local em seu computador.</span><span class="sxs-lookup"><span data-stu-id="9bd91-230">If your app targets the Windows.Holographic device family, the [Windows App Certification Kit](https://msdn.microsoft.com/library/windows/apps/xaml/mt186449.aspx) will only run local static analysis tests on your PC.</span></span> <span data-ttu-id="9bd91-231">Não há testes serão executados em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9bd91-231">No tests will be run on your HoloLens.</span></span>

## <a name="see-also"></a><span data-ttu-id="9bd91-232">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bd91-232">See also</span></span>
* [<span data-ttu-id="9bd91-233">Enviar um aplicativo para a Windows Store</span><span class="sxs-lookup"><span data-stu-id="9bd91-233">Submitting an app to the Windows Store</span></span>](submitting-an-app-to-the-microsoft-store.md)
---
title: O que é um holograma?
description: O HoloLens permite exibir e interagir com hologramas tridimensionais, objetos compostos de luz e som que aparecem no mundo todo.
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, HoloLens, hologramas, design, interação
ms.openlocfilehash: 5fb3aff3f59d0999676356d257b72f286a8d7adf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435085"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="b8667-104">O que é um holograma?</span><span class="sxs-lookup"><span data-stu-id="b8667-104">What is a hologram?</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


<span data-ttu-id="b8667-105">O HoloLens permite criar **hologramas**, objetos compostos de luz e som que aparecem no mundo, assim como se fossem objetos reais.</span><span class="sxs-lookup"><span data-stu-id="b8667-105">HoloLens lets you create **holograms**, objects made of light and sound that appear in the world around you, just as if they were real objects.</span></span> <span data-ttu-id="b8667-106">Os hologramas respondem aos seus [olhar](gaze-and-commit.md), [gestos](gaze-and-commit.md#composite-gestures) e [comandos de voz](voice-input.md)e podem interagir com [superfícies reais](spatial-mapping.md) em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="b8667-106">Holograms respond to your [gaze](gaze-and-commit.md), [gestures](gaze-and-commit.md#composite-gestures) and [voice commands](voice-input.md), and can interact with [real-world surfaces](spatial-mapping.md) around you.</span></span> <span data-ttu-id="b8667-107">Com os hologramas, você pode criar objetos digitais que fazem parte do seu mundo.</span><span class="sxs-lookup"><span data-stu-id="b8667-107">With holograms, you can create digital objects that are part of your world.</span></span>

<br>


## <a name="device-support"></a><span data-ttu-id="b8667-108">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="b8667-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b8667-109"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="b8667-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b8667-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b8667-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b8667-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b8667-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="b8667-112"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="b8667-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b8667-113">Hologramas</span><span class="sxs-lookup"><span data-stu-id="b8667-113">Holograms</span></span></td>
        <td><span data-ttu-id="b8667-114">✔️</span><span class="sxs-lookup"><span data-stu-id="b8667-114">✔️</span></span></td>
        <td><span data-ttu-id="b8667-115">✔️</span><span class="sxs-lookup"><span data-stu-id="b8667-115">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="b8667-116">Um holograma é formado de luz e som</span><span class="sxs-lookup"><span data-stu-id="b8667-116">A hologram is made of light and sound</span></span>

<span data-ttu-id="b8667-117">Os hologramas que o HoloLens [renderiza](rendering.md) aparecem no quadro Holographic diretamente na frente dos olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="b8667-117">The holograms that HoloLens [renders](rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="b8667-118">Os hologramas adicionam luz ao seu mundo, o que significa que você vê a luz da tela e a luz de seus arredores.</span><span class="sxs-lookup"><span data-stu-id="b8667-118">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="b8667-119">O HoloLens não remove a luz dos seus olhos, portanto, os hologramas não podem ser renderizados com a cor preta.</span><span class="sxs-lookup"><span data-stu-id="b8667-119">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="b8667-120">Em vez disso, o conteúdo preto aparece como transparente.</span><span class="sxs-lookup"><span data-stu-id="b8667-120">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="b8667-121">Os hologramas podem ter várias aparências e comportamentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="b8667-121">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="b8667-122">Alguns são realísticos e sólidos, e outros são animados e o Ethereal.</span><span class="sxs-lookup"><span data-stu-id="b8667-122">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="b8667-123">Os hologramas podem destacar recursos no seu ambiente e podem ser elementos na interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8667-123">Holograms can highlight features in your surroundings, and they can be elements in your app's user interface.</span></span>

![Mãos manipulando um holograma](images/hologram-hands-940px.jpg)

<span data-ttu-id="b8667-125">Os hologramas também podem fazer [sons](spatial-sound.md), que parecerão vir de um local específico em seus arredores.</span><span class="sxs-lookup"><span data-stu-id="b8667-125">Holograms can also make [sounds](spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="b8667-126">No HoloLens, o som vem de dois alto-falantes que estão localizados diretamente acima de seus ouvidos, sem cobri-los.</span><span class="sxs-lookup"><span data-stu-id="b8667-126">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="b8667-127">Semelhante às telas, os alto-falantes são aditivos, apresentando novos sons sem bloquear os sons do seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="b8667-127">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="b8667-128">Um holograma pode ser colocado no mundo ou em uma marca junto com você</span><span class="sxs-lookup"><span data-stu-id="b8667-128">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="b8667-129">Quando você tem um local específico onde deseja um holograma, você pode [colocá](coordinate-systems.md) -lo precisamente no mundo.</span><span class="sxs-lookup"><span data-stu-id="b8667-129">When you have a particular location where you want a hologram, you can [place](coordinate-systems.md) it precisely there in the world.</span></span> <span data-ttu-id="b8667-130">À medida que você percorre esse holograma, ele parecerá estável em relação ao mundo em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="b8667-130">As you walk around that hologram, it will appear stable relative to the world around you.</span></span> <span data-ttu-id="b8667-131">Se você usar uma [âncora espacial](coordinate-systems.md#spatial-anchors) para fixar esse objeto firmemente ao mundo, o sistema poderá até mesmo lembrar onde você o deixou quando voltar mais tarde.</span><span class="sxs-lookup"><span data-stu-id="b8667-131">If you use a [spatial anchor](coordinate-systems.md#spatial-anchors) to pin that object firmly to the world, the system can even remember where you left it when you come back later.</span></span>

![Dois homens usando o layout do Microsoft Dynamics 365 em um espaço de varejo](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="b8667-133">Em vez disso, alguns hologramas seguem o usuário.</span><span class="sxs-lookup"><span data-stu-id="b8667-133">Some holograms follow the user instead.</span></span> <span data-ttu-id="b8667-134">Esses hologramas de marcas são posicionados em relação ao usuário, independentemente de onde eles se movimentam.</span><span class="sxs-lookup"><span data-stu-id="b8667-134">These tag-along holograms position themselves relative to the user, no matter where they walk.</span></span> <span data-ttu-id="b8667-135">Você pode até mesmo optar por trazer um holograma com você por um tempo e colocá-lo na parede quando chegar a outra sala.</span><span class="sxs-lookup"><span data-stu-id="b8667-135">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="b8667-136">**Práticas recomendadas**</span><span class="sxs-lookup"><span data-stu-id="b8667-136">**Best practices**</span></span>
* <span data-ttu-id="b8667-137">Alguns cenários podem exigir que os hologramas permaneçam facilmente detectáveis ou visíveis em toda a experiência.</span><span class="sxs-lookup"><span data-stu-id="b8667-137">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="b8667-138">Há duas abordagens de alto nível para esse tipo de posicionamento.</span><span class="sxs-lookup"><span data-stu-id="b8667-138">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="b8667-139">Vamos chamá-los de **"display-Locked"** e **"Body-Locked"** .</span><span class="sxs-lookup"><span data-stu-id="b8667-139">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="b8667-140">O conteúdo bloqueado de exibição é posicionado "bloqueado" na tela do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b8667-140">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="b8667-141">Isso é complicado por vários motivos, incluindo uma sensação não natural de "clingyness" que torna muitos usuários frustrados e querendo "agite-los".</span><span class="sxs-lookup"><span data-stu-id="b8667-141">This is tricky for a number of reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="b8667-142">Em geral, muitos designers acharam melhor evitar conteúdo de bloqueio de exibição.</span><span class="sxs-lookup"><span data-stu-id="b8667-142">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="b8667-143">A abordagem de corpo bloqueado é muito mais forgivable.</span><span class="sxs-lookup"><span data-stu-id="b8667-143">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="b8667-144">O bloqueio de corpo é quando um holograma é vinculado ao corpo do usuário ou ao vetor olhar, mas está posicionado no espaço 3D em todo o usuário.</span><span class="sxs-lookup"><span data-stu-id="b8667-144">Body-locking is when a hologram is tethered to the user's body or gaze vector, but is positioned in 3d space around the user.</span></span> <span data-ttu-id="b8667-145">Muitas experiências adotaram um comportamento de bloqueio de corpo onde o holograma "segue" os usuários olhar, o que permite ao usuário girar seu corpo e percorrer o espaço sem perder o holograma.</span><span class="sxs-lookup"><span data-stu-id="b8667-145">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="b8667-146">Incorporar um atraso ajuda o movimento do holograma a se sentir mais natural.</span><span class="sxs-lookup"><span data-stu-id="b8667-146">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="b8667-147">Por exemplo, alguma interface do usuário principal do sistema operacional Windows Holographic usa uma variação no bloqueio de corpo que segue o olhar do usuário com um atraso de AdaBoost e elástico, enquanto o usuário transforma sua cabeça.</span><span class="sxs-lookup"><span data-stu-id="b8667-147">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="b8667-148">Coloque o holograma em uma distância de exibição confortável, normalmente, cerca de 1-2 metros longe do início.</span><span class="sxs-lookup"><span data-stu-id="b8667-148">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="b8667-149">Forneça uma quantidade de descompasso para elementos que devem estar continuamente no quadro Holographic ou considere animar seu conteúdo para um lado da exibição quando o usuário alterar seu ponto de vista.</span><span class="sxs-lookup"><span data-stu-id="b8667-149">Provide an amount of drift for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="b8667-150">**Coloque os hologramas na zona ideal-entre 1,25 m e 5 min**</span><span class="sxs-lookup"><span data-stu-id="b8667-150">**Place holograms in the optimal zone - between 1.25m and 5m**</span></span>

<span data-ttu-id="b8667-151">Dois medidores são os mais ideais e a experiência diminuirá quanto mais perto você chegar de um medidor.</span><span class="sxs-lookup"><span data-stu-id="b8667-151">Two meters is the most optimal, and the experience will degrade the closer you get from one meter.</span></span> <span data-ttu-id="b8667-152">Às distâncias mais próximas de um medidor, os hologramas que se movem regularmente em profundidade têm maior probabilidade de serem problemáticos do que os hologramas fixos.</span><span class="sxs-lookup"><span data-stu-id="b8667-152">At distances nearer than one meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="b8667-153">Considere recortar ou desbotar seu conteúdo de forma elegante quando ficar muito próximo, para não desconectar o usuário em uma experiência inesperada.</span><span class="sxs-lookup"><span data-stu-id="b8667-153">Consider gracefully clipping or fading out your content when it gets too close so as not to jar the user into an unexpected experience.</span></span>

![Distância ideal para colocar os hologramas do usuário.](images/distanceguiderendering-950px.png)

<br>

---


## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="b8667-155">Um holograma interage com você e seu mundo</span><span class="sxs-lookup"><span data-stu-id="b8667-155">A hologram interacts with you and your world</span></span>

<span data-ttu-id="b8667-156">Os hologramas não são apenas sobre luz e som; Eles também são uma parte ativa do seu mundo.</span><span class="sxs-lookup"><span data-stu-id="b8667-156">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="b8667-157">Olhar com um holograma e um gesto com sua mão, e um holograma pode começar a acompanhá-lo.</span><span class="sxs-lookup"><span data-stu-id="b8667-157">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="b8667-158">Dê um comando de voz para um holograma e ele pode responder.</span><span class="sxs-lookup"><span data-stu-id="b8667-158">Give a voice command to a hologram, and it can reply.</span></span>

![Grupo de funcionários de utilitário do governo usando o Microsoft HoloLens 2 para colaborar em um projeto de desenvolvimento de farm de vento](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="b8667-160">Os hologramas permitem interações pessoais que não são possíveis em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="b8667-160">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="b8667-161">Como o HoloLens sabe onde ele está no mundo, um caractere Holographic pode examiná-lo diretamente nos olhos à medida que você percorre a sala.</span><span class="sxs-lookup"><span data-stu-id="b8667-161">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="b8667-162">Um holograma também pode interagir com seus arredores.</span><span class="sxs-lookup"><span data-stu-id="b8667-162">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="b8667-163">Por exemplo, você pode inserir uma bola saltando Holographic acima de uma tabela.</span><span class="sxs-lookup"><span data-stu-id="b8667-163">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="b8667-164">Em seguida, com um [toque de ar](gaze-and-commit.md#composite-gestures), observe o salto de bola e faça o som quando ele atingir a tabela.</span><span class="sxs-lookup"><span data-stu-id="b8667-164">Then, with an [air tap](gaze-and-commit.md#composite-gestures), watch the ball bounce and make sound when it hits the table.</span></span>

<span data-ttu-id="b8667-165">Os hologramas também podem ser obstruídodos por objetos do mundo real.</span><span class="sxs-lookup"><span data-stu-id="b8667-165">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="b8667-166">Por exemplo, um caractere Holographic pode percorrer uma porta e atrás de uma parede, fora de sua visão.</span><span class="sxs-lookup"><span data-stu-id="b8667-166">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="b8667-167">**Dicas para integrar hologramas e o mundo real**</span><span class="sxs-lookup"><span data-stu-id="b8667-167">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="b8667-168">Alinhar às regras do Gravitational torna os hologramas mais fáceis de se relacionar e mais verossímeis.</span><span class="sxs-lookup"><span data-stu-id="b8667-168">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="b8667-169">por exemplo: Coloque um cachorro Holographic no chão & um vaso na tabela em vez de tê-los flutuantes no espaço.</span><span class="sxs-lookup"><span data-stu-id="b8667-169">eg: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="b8667-170">Muitos designers descobriram que eles podem ainda mais believably integrar hologramas criando uma "sombra negativa" na superfície em que o holograma está sentado.</span><span class="sxs-lookup"><span data-stu-id="b8667-170">Many designers have found that they can even more believably integrate holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="b8667-171">Eles fazem isso criando um brilho suave no chão ao lado do holograma e subtraindo a "sombra" do brilho.</span><span class="sxs-lookup"><span data-stu-id="b8667-171">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="b8667-172">O brilho suave se integra com a luz do mundo real e a sombra aterra o holograma no ambiente.</span><span class="sxs-lookup"><span data-stu-id="b8667-172">The soft glow integrates with the light from the real world and the shadow grounds the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a><span data-ttu-id="b8667-173">Um holograma é qualquer coisa</span><span class="sxs-lookup"><span data-stu-id="b8667-173">A hologram is whatever</span></span> <br><span data-ttu-id="b8667-174">Você pode sonho</span><span class="sxs-lookup"><span data-stu-id="b8667-174">you can dream up</span></span><br>
        <span data-ttu-id="b8667-175">Como desenvolvedor de Holographic, você tem a capacidade de dividir sua criatividade em telas 2D e em seu mundo.</span><span class="sxs-lookup"><span data-stu-id="b8667-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="b8667-176">O que *você* vai criar?</span><span class="sxs-lookup"><span data-stu-id="b8667-176">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="b8667-177">![de espaço](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="b8667-177">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="b8667-178">![Holographic imaginários mundiais na sala de vida](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8667-178">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="see-also"></a><span data-ttu-id="b8667-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8667-179">See also</span></span>
* [<span data-ttu-id="b8667-180">Expanda seu processo de design</span><span class="sxs-lookup"><span data-stu-id="b8667-180">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)
* [<span data-ttu-id="b8667-181">Som espacial</span><span class="sxs-lookup"><span data-stu-id="b8667-181">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="b8667-182">Cor, luz e materiais</span><span class="sxs-lookup"><span data-stu-id="b8667-182">Color, light and materials</span></span>](color,-light-and-materials.md)

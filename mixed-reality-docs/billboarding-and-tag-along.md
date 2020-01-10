---
title: Contorno e marcação
description: Os objetos com o mural sempre se orientam para enfrentar o usuário.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade misturada do Windows, mensagem de contorno
ms.openlocfilehash: 24c4ca8bdc3c6ea1081311102204d4a7f5a95425
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723175"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="f2049-104">Contorno e marcação</span><span class="sxs-lookup"><span data-stu-id="f2049-104">Billboarding and tag-along</span></span>

<br>

<img src="images/UX/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="f2049-105">O que é o mural?</span><span class="sxs-lookup"><span data-stu-id="f2049-105">What is billboarding?</span></span>

<span data-ttu-id="f2049-106">A mensagem é um conceito comportamental que pode ser aplicado a objetos em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="f2049-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="f2049-107">Os objetos com o mural sempre se orientam para enfrentar o usuário.</span><span class="sxs-lookup"><span data-stu-id="f2049-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="f2049-108">Isso é especialmente útil com os sistemas de texto e de menu em que os objetos estáticos colocados no ambiente do usuário (bloqueado pelo mundo) seriam obscuros ou ilegíveis se um usuário fosse migrado.</span><span class="sxs-lookup"><span data-stu-id="f2049-108">This is especially helpful with text and menuing systems where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable if a user were to move around.</span></span>

<span data-ttu-id="f2049-109">Os objetos com o mural habilitado podem girar livremente no ambiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="f2049-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="f2049-110">Eles também podem ser restritos a um único eixo, dependendo das considerações de design.</span><span class="sxs-lookup"><span data-stu-id="f2049-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="f2049-111">Lembre-se de que os objetos configurados podem recortar ou occlude-los se forem colocados muito próximos a outros objetos, ou no HoloLens, fechar as superfícies digitalizadas.</span><span class="sxs-lookup"><span data-stu-id="f2049-111">Keep in mind, billboarded objects may clip or occlude themselves if they are placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="f2049-112">Para evitar isso, pense na superfície total que um objeto pode produzir quando girado no eixo habilitado para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="f2049-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="f2049-113">O que é uma marca?</span><span class="sxs-lookup"><span data-stu-id="f2049-113">What is a tag-along?</span></span>

<span data-ttu-id="f2049-114">A marcação é um conceito comportamental que pode ser adicionado a hologramas.</span><span class="sxs-lookup"><span data-stu-id="f2049-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="f2049-115">Um objeto de marca ao longo das tentativas de permanecer em um intervalo que permite que o usuário interaja confortavelmente.</span><span class="sxs-lookup"><span data-stu-id="f2049-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="f2049-116">![o painel Pins do HoloLens é um ótimo exemplo de como a tag se comporta](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f2049-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="f2049-117">*O menu Iniciar do HoloLens é um ótimo exemplo de comportamento de marcação*</span><span class="sxs-lookup"><span data-stu-id="f2049-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="f2049-118">Os objetos de marcação têm parâmetros que podem ajustar a forma com que se comportam.</span><span class="sxs-lookup"><span data-stu-id="f2049-118">Tag-along objects have parameters which can fine-tune the way they behave.</span></span> <span data-ttu-id="f2049-119">O conteúdo pode estar dentro ou fora da linha de visão do usuário, conforme desejado, enquanto o usuário se move em torno de seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="f2049-119">Content can be in or out of the user’s line of sight as desired while the user moves around their environment.</span></span> <span data-ttu-id="f2049-120">À medida que o usuário se move, o conteúdo tentará permanecer dentro do periferia do usuário, deslizando para a borda da exibição, dependendo da rapidez com que um usuário se move pode deixar o conteúdo temporariamente fora da exibição.</span><span class="sxs-lookup"><span data-stu-id="f2049-120">As the user moves, the content will attempt to stay within the user’s periphery by sliding towards the edge of the view, depending on how quickly a user moves may leave the content temporarily out of view.</span></span> <span data-ttu-id="f2049-121">Quando o usuário gazes em direção ao objeto de marca, ele é mais totalmente na exibição.</span><span class="sxs-lookup"><span data-stu-id="f2049-121">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="f2049-122">Imagine que o conteúdo esteja sempre sendo "um relance" para que os usuários nunca se esqueçam em que direção seu conteúdo está.</span><span class="sxs-lookup"><span data-stu-id="f2049-122">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="f2049-123">Parâmetros adicionais podem fazer com que a marca de objeto seja anexada à cabeça do usuário por uma faixa de borracha.</span><span class="sxs-lookup"><span data-stu-id="f2049-123">Additional parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="f2049-124">A aceleração ou a desaceleração proporciona peso ao objeto, fazendo com que ele fique mais fisicamente presente.</span><span class="sxs-lookup"><span data-stu-id="f2049-124">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="f2049-125">Esse comportamento de mola é uma forma que ajuda o usuário a criar um modelo mental preciso de como o Tag-by funciona.</span><span class="sxs-lookup"><span data-stu-id="f2049-125">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="f2049-126">O áudio ajuda a fornecer capacidades adicionais para quando os usuários têm objetos no modo de marca.</span><span class="sxs-lookup"><span data-stu-id="f2049-126">Audio helps provide additional affordances for when users have objects in tag-along mode.</span></span> <span data-ttu-id="f2049-127">O áudio deve reforçar a velocidade de movimento; uma rodada de cabeça rápida deve fornecer um efeito de som mais perceptível enquanto a movimentação em uma velocidade natural deve ter um áudio mínimo se houver algum efeito.</span><span class="sxs-lookup"><span data-stu-id="f2049-127">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect while walking at a natural speed should have minimal audio if any effects at all.</span></span>

<span data-ttu-id="f2049-128">Assim como o conteúdo realmente bloqueado, os objetos de marca podem se comprovar de forma exagerada ou nauseating se se moverem intensamente ou se acabarem muito na exibição do usuário.</span><span class="sxs-lookup"><span data-stu-id="f2049-128">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="f2049-129">Como um usuário procura e, em seguida, pára rapidamente, seus sentidos dizem que eles foram interrompidos.</span><span class="sxs-lookup"><span data-stu-id="f2049-129">As a user looks around and then quickly stop, their senses tell them they have stopped.</span></span> <span data-ttu-id="f2049-130">Seu saldo informa que sua cabeça parou de ser ativada, bem como sua visão vê o mundo parar de ligar.</span><span class="sxs-lookup"><span data-stu-id="f2049-130">Their balance informs them that their head has stopped turning as well as their vision sees the world stop turning.</span></span> <span data-ttu-id="f2049-131">No entanto, se a marca ainda mantiver a movimentação quando o usuário for interrompido, ele poderá confundir seus sentidos.</span><span class="sxs-lookup"><span data-stu-id="f2049-131">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="f2049-132">Contorno e marcação em MRTK (Kit de ferramentas de realidade misturada) para o Unity</span><span class="sxs-lookup"><span data-stu-id="f2049-132">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="f2049-133">O **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts para o comportamento de etiqueta e de contorno.</span><span class="sxs-lookup"><span data-stu-id="f2049-133">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="f2049-134">Basta atribuir o script Billboard.cs a qualquer objeto para adicionar o comportamento de mensagem e fazer com que o objeto sempre fique à frente.</span><span class="sxs-lookup"><span data-stu-id="f2049-134">Simply assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="f2049-135">Para adicionar o comportamento de marca, use o script RadialView.cs.</span><span class="sxs-lookup"><span data-stu-id="f2049-135">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="f2049-136">Você pode ajustar várias opções, como lerping time, Distance e diploma.</span><span class="sxs-lookup"><span data-stu-id="f2049-136">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="f2049-137">MRTK-solucionador de exibição radial</span><span class="sxs-lookup"><span data-stu-id="f2049-137">MRTK - Radial View Solver</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [<span data-ttu-id="f2049-138">MRTK-script do mural</span><span class="sxs-lookup"><span data-stu-id="f2049-138">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="f2049-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="f2049-139">See also</span></span>

* [<span data-ttu-id="f2049-140">Cursores</span><span class="sxs-lookup"><span data-stu-id="f2049-140">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="f2049-141">Raio de mão</span><span class="sxs-lookup"><span data-stu-id="f2049-141">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="f2049-142">Botão</span><span class="sxs-lookup"><span data-stu-id="f2049-142">Button</span></span>](button.md)
* [<span data-ttu-id="f2049-143">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="f2049-143">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f2049-144">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="f2049-144">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="f2049-145">Manipulação</span><span class="sxs-lookup"><span data-stu-id="f2049-145">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f2049-146">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="f2049-146">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="f2049-147">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="f2049-147">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="f2049-148">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="f2049-148">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="f2049-149">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="f2049-149">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="f2049-150">Teclado</span><span class="sxs-lookup"><span data-stu-id="f2049-150">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="f2049-151">Dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="f2049-151">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="f2049-152">Slate</span><span class="sxs-lookup"><span data-stu-id="f2049-152">Slate</span></span>](slate.md)
* [<span data-ttu-id="f2049-153">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="f2049-153">Slider</span></span>](slider.md)
* [<span data-ttu-id="f2049-154">Sombreador</span><span class="sxs-lookup"><span data-stu-id="f2049-154">Shader</span></span>](shader.md)
* [<span data-ttu-id="f2049-155">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="f2049-155">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="f2049-156">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="f2049-156">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="f2049-157">Magnetismo de superfície</span><span class="sxs-lookup"><span data-stu-id="f2049-157">Surface magnetism</span></span>](surface-magnetism.md)

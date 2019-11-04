---
title: Escala
description: Para exibir conteúdo com aparência realista no formulário holográfico é fundamental imitar, do modo mais próximo possível, as estatísticas visuais do mundo real.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, estilo, design
ms.openlocfilehash: eeec28fbf98cf4386a57cde4452cd3f8977d7780
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437511"
---
# <a name="scale"></a><span data-ttu-id="94e99-104">Escala</span><span class="sxs-lookup"><span data-stu-id="94e99-104">Scale</span></span>

<span data-ttu-id="94e99-105">Para exibir conteúdo com aparência realista no formulário holográfico é fundamental imitar, do modo mais próximo possível, as estatísticas visuais do mundo real.</span><span class="sxs-lookup"><span data-stu-id="94e99-105">A key to displaying content that looks realistic in holographic form is to mimic the visual statistics of the real world as closely as possible.</span></span> <span data-ttu-id="94e99-106">Isso significa incorporar o máximo de dicas visuais que podem nos ajudar (no mundo real) a entender onde estão os objetos, quão grandes são e do que eles são feitos.</span><span class="sxs-lookup"><span data-stu-id="94e99-106">This means incorporating as many of the visual cues as we can that help us (in the real world) understand where objects are, how big they are, and what they’re made of.</span></span> <span data-ttu-id="94e99-107">A escala de um objeto é uma das mais importantes das indicações visuais, dando a um visualizador um sentido do tamanho de um objeto, bem como de indicações para seu local (especialmente para objetos que têm um tamanho conhecido).</span><span class="sxs-lookup"><span data-stu-id="94e99-107">The scale of an object is one of the most important of those visual cues, giving a viewer a sense of the size of an object as well as cues to its location (especially for objects which have a known size).</span></span> <span data-ttu-id="94e99-108">Além disso, a exibição de objetos em escala real foi vista como um dos principais diferenciais de experiência para a realidade misturada em geral – algo que não era possível na exibição baseada em tela anteriormente.</span><span class="sxs-lookup"><span data-stu-id="94e99-108">Further, viewing objects at real scale has been seen as one of the key experience differentiators for mixed reality in general – something that hasn’t been possible on screen-based viewing previously.</span></span>

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a><span data-ttu-id="94e99-109">Como sugerir a escala de objetos e ambientes</span><span class="sxs-lookup"><span data-stu-id="94e99-109">How to suggest the scale of objects and environments</span></span>

<span data-ttu-id="94e99-110">Há várias maneiras de sugerir a escala de um objeto, alguns dos quais têm possíveis efeitos em outros fatores de perceptiva.</span><span class="sxs-lookup"><span data-stu-id="94e99-110">There are many ways to suggest the scale of an object, some of which have possible effects on other perceptual factors.</span></span> <span data-ttu-id="94e99-111">A chave a é simplesmente exibir objetos com um tamanho "real" e manter esse tamanho realista à medida que os usuários se movem.</span><span class="sxs-lookup"><span data-stu-id="94e99-111">The key one is to simply display objects at a ‘real’ size, and maintain that realistic size as users move.</span></span> <span data-ttu-id="94e99-112">Isso significa que os hologramas ocuparão uma quantidade diferente do ângulo visual do usuário de um usuário à medida que eles ficarem mais próximos ou mais distantes, da mesma forma que os objetos reais.</span><span class="sxs-lookup"><span data-stu-id="94e99-112">This means holograms will take up a different amount of a user’s visual angle of a user as they come closer or further away, the same way that real objects do.</span></span>

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a><span data-ttu-id="94e99-113">Utilize a distância dos objetos conforme eles são apresentados ao usuário</span><span class="sxs-lookup"><span data-stu-id="94e99-113">Utilize the distance of objects as they are presented to the user</span></span>

<span data-ttu-id="94e99-114">Um método comum é utilizar a distância dos objetos conforme eles são apresentados ao usuário.</span><span class="sxs-lookup"><span data-stu-id="94e99-114">One common method is to utilize the distance of objects as they are presented to the user.</span></span> <span data-ttu-id="94e99-115">Por exemplo, considere a visualização de um carro de família grande na frente do usuário.</span><span class="sxs-lookup"><span data-stu-id="94e99-115">For example, consider visualizing a large family car in front of the user.</span></span> <span data-ttu-id="94e99-116">Se o carro estivesse diretamente em frente, dentro do comprimento do ARM, seria muito grande para caber no campo de exibição do usuário.</span><span class="sxs-lookup"><span data-stu-id="94e99-116">If the car were directly in front of them, within arm’s length, it would be too large to fit in the user’s field of view.</span></span> <span data-ttu-id="94e99-117">Isso exige que o usuário mova a cabeça e o corpo para entender todo o objeto.</span><span class="sxs-lookup"><span data-stu-id="94e99-117">This would require the user to move their head and body to understand the entirety of the object.</span></span> <span data-ttu-id="94e99-118">Se o carro fosse colocado mais distante (em toda a sala), o usuário pode estabelecer uma noção de escala ao ver todo o objeto em seu campo de exibição e, em seguida, se aproximar mais perto dele para inspecionar áreas em detalhes.</span><span class="sxs-lookup"><span data-stu-id="94e99-118">If the car were placed further away (across the room), the user can establish a sense of scale by seeing the entirety of the object in their field of view, then moving themselves closer to it to inspect areas in detail.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="94e99-119">A **[Volvo usou essa técnica para criar uma](https://www.youtube.com/watch?v=DilzwF90vec)** experiência de showroom para um novo carro, utilizando a escala do carro Holographic de uma forma que parecia realista e intuitiva ao usuário.</span><span class="sxs-lookup"><span data-stu-id="94e99-119">**[Volvo used this technique to create a showroom](https://www.youtube.com/watch?v=DilzwF90vec)** experience for a new car, utilizing the scale of the holographic car in a way that felt realistic and intuitive to the user.</span></span> <span data-ttu-id="94e99-120">A experiência começa com um holograma do carro em uma tabela física, permitindo que o usuário entenda o tamanho total e a forma do modelo.</span><span class="sxs-lookup"><span data-stu-id="94e99-120">The experience begins with a hologram of the car on a physical table, allowing the user to understand the total size and shape of the model.</span></span> <span data-ttu-id="94e99-121">Mais tarde, na experiência, o carro se expande para uma escala maior (além do tamanho do campo de exibição do dispositivo), mas, como o usuário já adquiriu um quadro de referência do modelo menor, ele pode navegar adequadamente pelos recursos do carro.</span><span class="sxs-lookup"><span data-stu-id="94e99-121">Later in the experience, the car expands to a larger scale (beyond the size of the device's field of view) but, since the user already acquired a frame of reference from the smaller model, they can adequately navigate around features of the car.</span></span><br>
        <br>
        <span data-ttu-id="94e99-122">*Imagem: experiência de carros Volvo para o HoloLens*</span><span class="sxs-lookup"><span data-stu-id="94e99-122">*Image: Volvo Cars experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![Experiência de carros Volvo para o HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a><span data-ttu-id="94e99-124">Usar hologramas para modificar o espaço real do usuário</span><span class="sxs-lookup"><span data-stu-id="94e99-124">Use holograms to modify the user's real space</span></span>

<span data-ttu-id="94e99-125">Outro método é usar hologramas para modificar o espaço real do usuário, substituindo as paredes ou os tetos existentes por ambientes ou acrescentando "buracos" ou "Windows", permitindo que os objetos de tamanho mais longo pareçam "dividir" o espaço físico.</span><span class="sxs-lookup"><span data-stu-id="94e99-125">Another method is to use holograms to modify the user's real space, replacing the existing walls or ceilings with environments or appending ‘holes’ or ‘windows’, allowing over-sized objects to seemingly 'break-through' the physical space.</span></span> <span data-ttu-id="94e99-126">Por exemplo, uma árvore grande pode não se ajustar à maioria das salas de vida dos usuários, mas ao colocar um céu virtual em seu teto, o espaço físico se expande para a máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="94e99-126">For example, a large tree might not fit in most users’ living rooms, but by putting a virtual sky on their ceiling, the physical space expands into the virtual.</span></span> <span data-ttu-id="94e99-127">Isso permite que o usuário percorra a base da árvore virtual e reúna uma noção de como ela seria exibida na vida real e, em seguida, veja que ela se estende muito além do espaço físico da sala.</span><span class="sxs-lookup"><span data-stu-id="94e99-127">This allows the user to walk around the base of the virtual tree, and gather a sense of scale of how it would appear in real life, then look up to see it extend far beyond the physical space of the room.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="94e99-128">**[Minecraft desenvolveu uma experiência de conceito](https://minecraft.net/)** usando uma técnica semelhante.</span><span class="sxs-lookup"><span data-stu-id="94e99-128">**[Minecraft developed a concept experiences](https://minecraft.net/)** using a similar technique.</span></span> <span data-ttu-id="94e99-129">Ao adicionar uma janela virtual a uma superfície física em uma sala, os objetos existentes na sala são colocados no contexto de um ambiente amplamente maior, além das limitações de escala física da sala.</span><span class="sxs-lookup"><span data-stu-id="94e99-129">By adding a virtual window to a physical surface in a room, the existing objects in the room are placed in the context of a vastly larger environment, beyond the physical scale limitations of the room.</span></span><br>
        <br>
        <span data-ttu-id="94e99-130">*Imagem: experiência de conceito de Minecraft para o HoloLens*</span><span class="sxs-lookup"><span data-stu-id="94e99-130">*Image: Minecraft concept experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![Experiência de conceito de Minecraft para o HoloLens](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a><span data-ttu-id="94e99-132">Experimentando a escala</span><span class="sxs-lookup"><span data-stu-id="94e99-132">Experimenting with scale</span></span>

<span data-ttu-id="94e99-133">Em alguns casos, os designers experimentaram modificar a escala (alterando o tamanho ' real ' exibido do objeto) mantendo, ao mesmo tempo, uma única posição do objeto para aproximar um objeto que está ficando mais próximo ou mais de um visualizador sem qualquer movimento real.</span><span class="sxs-lookup"><span data-stu-id="94e99-133">In some cases, designers have experimented with modifying the scale (by changing the displayed ‘real’ size of the object) while maintaining a single position of the object, to approximate an object getting closer or further to a viewer without any actual movement.</span></span> <span data-ttu-id="94e99-134">Isso foi testado em alguns casos como uma maneira de simular a visualização de itens e, ao mesmo tempo, respeitar possíveis limitações de conforto de exibir conteúdo virtual mais próximo do que a "zona de conforto" sugere.</span><span class="sxs-lookup"><span data-stu-id="94e99-134">This was tested in some cases as a way to simulate up-close viewing of items while still respecting potential comfort limitations of viewing virtual content closer than the “zone of comfort” would suggest.</span></span>

<span data-ttu-id="94e99-135">No entanto, isso pode criar alguns artefatos possíveis na experiência:</span><span class="sxs-lookup"><span data-stu-id="94e99-135">This can create a few possible artifacts in the experience however:</span></span>
* <span data-ttu-id="94e99-136">Para objetos virtuais que representam algum objeto com um tamanho "conhecido" para o visualizador, alterar a escala sem alterar a posição leva a indicações visuais conflitantes – os olhos ainda podem "ver" o objeto em alguma profundidade devido a indicações de Vergence (consulte o [conforto](comfort.md) artigo para obter mais informações sobre isso), mas o tamanho atua como uma indicação monocular de que o objeto pode estar ficando mais próximo.</span><span class="sxs-lookup"><span data-stu-id="94e99-136">For virtual objects that represent some object with a ‘known’ size to the viewer, changing the scale without changing the position leads to conflicting visual cues – the eyes may still ‘see’ the object at some depth due to vergence cues (see the [Comfort](comfort.md) article for more on this), but the size acts as a monocular cue that the object might be getting closer.</span></span> <span data-ttu-id="94e99-137">Essas indicações conflitantes levam a percepções confusas – os visualizadores geralmente veem o objeto como estando em vigor (devido à indicação de profundidade constante), mas crescendo rapidamente.</span><span class="sxs-lookup"><span data-stu-id="94e99-137">These conflicting cues lead to confused perceptions – viewers often see the object as staying in place (due to the constant depth cue) but growing rapidly.</span></span>
* <span data-ttu-id="94e99-138">Em alguns casos, a alteração de escala é vista como uma indicação ' surgindo ', em que o objeto pode ou não ser visto para alterar a escala por um visualizador, mas parece estar se movendo diretamente para os olhos do visualizador (o que pode ser um sensação desconfortável).</span><span class="sxs-lookup"><span data-stu-id="94e99-138">In some cases, change of scale is seen as a ‘looming’ cue instead, where the object may or may not be seen to change scale by a viewer, but does appear to be moving directly toward the viewer’s eyes (which can be an uncomfortable sensation).</span></span>
* <span data-ttu-id="94e99-139">Com superfícies de comparação no mundo real, tais alterações de dimensionamento às vezes são vistas como alteração na posição ao longo de vários eixos. os objetos podem parecer mais baixos em vez de avançar (semelhante em uma projeção 2D do movimento 3D em alguns casos).</span><span class="sxs-lookup"><span data-stu-id="94e99-139">With comparison surfaces in the real world, such scaling changes are sometimes seen as changing position along multiple axes – objects may appear to drop lower instead of moving closer (similar in a 2D projection of 3D movement in some cases).</span></span>
* <span data-ttu-id="94e99-140">Por fim, para objetos sem um tamanho "Real World" conhecido (por exemplo, formas arbitrárias com tamanhos arbitrários, elementos de interface do usuário, etc.), a escala de alteração pode funcionar funcionalmente como uma forma de imitar alterações em distância – os visualizadores não têm tantas indicações de cima para baixo pré-existentes pelas quais Entenda o tamanho ou o local verdadeiro do objeto, para que a escala possa ser processada como uma indicação mais importante.</span><span class="sxs-lookup"><span data-stu-id="94e99-140">Finally, for objects without a known ‘real world’ size (e.g. arbitrary shapes with arbitrary sizes, UI elements, etc.), changing scale may act functionally as a way to mimic changes in distance – viewers do not have as many preexisting top-down cues by which to understand the object’s true size or location, so the scale can be processed as a more important cue.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="94e99-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94e99-141">See also</span></span>
* [<span data-ttu-id="94e99-142">Cor, luz e materiais</span><span class="sxs-lookup"><span data-stu-id="94e99-142">Color, light and materials</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="94e99-143">Tipografia</span><span class="sxs-lookup"><span data-stu-id="94e99-143">Typography</span></span>](typography.md)
* [<span data-ttu-id="94e99-144">Projeto de som espacial</span><span class="sxs-lookup"><span data-stu-id="94e99-144">Spatial sound design</span></span>](spatial-sound-design.md)

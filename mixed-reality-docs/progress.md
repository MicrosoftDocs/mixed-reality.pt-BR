---
title: Exibindo progresso
description: Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realidade mista do Windows, design, controles, interface do usuário, UX
ms.openlocfilehash: aafcd8eebbabfc5b53d09348d513f62def909da6
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105984"
---
# <a name="progress-indicator"></a><span data-ttu-id="b8a4c-104">Indicador de progresso</span><span class="sxs-lookup"><span data-stu-id="b8a4c-104">Progress indicator</span></span>

<br>

<img src="images/UX/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="b8a4c-105">Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="b8a4c-106">Isso pode significar que o usuário não pode interagir com o aplicativo quando o indicador de progresso está visível e também pode indicar a duração do tempo de espera, dependendo do indicador usado.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="b8a4c-107">Tipo de progresso</span><span class="sxs-lookup"><span data-stu-id="b8a4c-107">Types of progress</span></span>

<span data-ttu-id="b8a4c-108">É importante fornecer as informações do usuário sobre o que está acontecendo.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-108">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="b8a4c-109">Em realidade misturada, os usuários podem ser facilmente distraídosdos por ambientes físicos ou objetos se seu aplicativo não fornecer bons comentários visuais.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-109">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="b8a4c-110">Para situações que levam alguns segundos, como quando os dados estão sendo carregados ou uma cena está atualizando, é recomendável mostrar um indicador visual.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-110">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="b8a4c-111">Há duas opções para mostrar ao usuário que uma operação está em andamento – uma **barra de progresso** ou um **anel de progresso**.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="b8a4c-112">Barra de progresso</span><span class="sxs-lookup"><span data-stu-id="b8a4c-112">Progress bar</span></span><br>
        <span data-ttu-id="b8a4c-113">Uma barra de progresso mostra a porcentagem concluída de uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="b8a4c-114">Ele deve ser usado durante uma operação cuja duração é conhecida (desterminada), mas o progresso não deve bloquear a interação do usuário com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-114">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="b8a4c-115">*Imagem: exemplo de barra de progresso no HoloLens*</span><span class="sxs-lookup"><span data-stu-id="b8a4c-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="b8a4c-116">![de espaço](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="b8a4c-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="b8a4c-117">![exemplo de barra de progresso no HoloLens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8a4c-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="b8a4c-118">Anel de progresso</span><span class="sxs-lookup"><span data-stu-id="b8a4c-118">Progress ring</span></span><br>
        <span data-ttu-id="b8a4c-119">Um anel de progresso tem apenas um estado indeterminado e deve ser usado quando qualquer interação adicional do usuário é bloqueada até que a operação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-119">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="b8a4c-120">*Imagem: exemplo de anel de andamento no HoloLens*</span><span class="sxs-lookup"><span data-stu-id="b8a4c-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="b8a4c-121">![de espaço](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="b8a4c-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="b8a4c-122">![exemplo de anel de progresso no HoloLens](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8a4c-122">![Progress ring example in HoloLens](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="b8a4c-123">Progresso com um objeto personalizado</span><span class="sxs-lookup"><span data-stu-id="b8a4c-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="b8a4c-124">Você pode adicionar à identidade da marca e personalidade do seu aplicativo Personalizando o controle de progresso com seus próprios objetos 2D/3D personalizados.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="b8a4c-125">*Imagem: progresso com o exemplo de malha personalizada no HoloLens*</span><span class="sxs-lookup"><span data-stu-id="b8a4c-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="b8a4c-126">![de espaço](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="b8a4c-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="b8a4c-127">![andamento com o exemplo de malha personalizada no HoloLens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8a4c-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="b8a4c-128">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="b8a4c-128">Best practices</span></span>
* <span data-ttu-id="b8a4c-129">Associe rigidamente a [mensagem ou a marca](billboarding-and-tag-along.md) à exibição do progresso, uma vez que o usuário pode mover facilmente o cabeçalho para o espaço vazio e perder o contexto.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="b8a4c-130">Seu aplicativo pode parecer que ele falhou se o usuário não conseguir ver nada.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="b8a4c-131">A cobrança e a marcação são criadas no pré-fabricado de progresso.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="b8a4c-132">É sempre bom fornecer informações de status sobre o que está acontecendo com o usuário.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="b8a4c-133">O progresso pré-fabricado fornece vários estilos visuais, incluindo o progresso padrão do Windows do tipo de toque para fornecer o status.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="b8a4c-134">Você também pode usar uma malha personalizada com uma animação se quiser que o estilo do seu progresso se alinhe à marca do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8a4c-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="b8a4c-135">Indicador de progresso em MRTK (Kit de ferramentas de realidade misturada) para Unity</span><span class="sxs-lookup"><span data-stu-id="b8a4c-135">Progress indicator in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="b8a4c-136">MRTK pré-fabricados indicador de progresso</span><span class="sxs-lookup"><span data-stu-id="b8a4c-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="b8a4c-137">Serviço de transição MRTK-Scene</span><span class="sxs-lookup"><span data-stu-id="b8a4c-137">MRTK - Scene transition service</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="b8a4c-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8a4c-138">See also</span></span>

* [<span data-ttu-id="b8a4c-139">Cursores</span><span class="sxs-lookup"><span data-stu-id="b8a4c-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="b8a4c-140">Raio da mão</span><span class="sxs-lookup"><span data-stu-id="b8a4c-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="b8a4c-141">Button</span><span class="sxs-lookup"><span data-stu-id="b8a4c-141">Button</span></span>](button.md)
* [<span data-ttu-id="b8a4c-142">Objeto interativo</span><span class="sxs-lookup"><span data-stu-id="b8a4c-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="b8a4c-143">Caixa delimitadora e barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="b8a4c-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="b8a4c-144">Manusei</span><span class="sxs-lookup"><span data-stu-id="b8a4c-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b8a4c-145">Menu lateral</span><span class="sxs-lookup"><span data-stu-id="b8a4c-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="b8a4c-146">Menu próximo</span><span class="sxs-lookup"><span data-stu-id="b8a4c-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="b8a4c-147">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="b8a4c-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="b8a4c-148">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="b8a4c-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="b8a4c-149">Teclado</span><span class="sxs-lookup"><span data-stu-id="b8a4c-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="b8a4c-150">Dessa</span><span class="sxs-lookup"><span data-stu-id="b8a4c-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="b8a4c-151">Slate</span><span class="sxs-lookup"><span data-stu-id="b8a4c-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="b8a4c-152">Slider</span><span class="sxs-lookup"><span data-stu-id="b8a4c-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="b8a4c-153">Mural e tag-along</span><span class="sxs-lookup"><span data-stu-id="b8a4c-153">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="b8a4c-154">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="b8a4c-154">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="b8a4c-155">Magnetism Surface</span><span class="sxs-lookup"><span data-stu-id="b8a4c-155">Surface magnetism</span></span>](surface-magnetism.md)

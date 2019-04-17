---
title: Exibindo o progresso
description: Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, controles da interface do usuário, experiência do usuário
ms.openlocfilehash: 9edddc7800f0d7334d1ceba97b9a06fd6d4580ac
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590592"
---
# <a name="displaying-progress"></a><span data-ttu-id="38e11-104">Exibindo o progresso</span><span class="sxs-lookup"><span data-stu-id="38e11-104">Displaying progress</span></span>

<span data-ttu-id="38e11-105">Um controle de progresso oferece feedback ao usuário que uma operação de execução longa está em andamento.</span><span class="sxs-lookup"><span data-stu-id="38e11-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="38e11-106">Isso pode significar que o usuário não pode interagir com o aplicativo quando o indicador de progresso está visível e também pode indicar a duração do tempo de espera, dependendo do indicador usado.</span><span class="sxs-lookup"><span data-stu-id="38e11-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="38e11-107">![Exemplo de anel de progresso no HoloLens](images/640px-progress-hero.jpg)</span><span class="sxs-lookup"><span data-stu-id="38e11-107">![Progress ring example in HoloLens](images/640px-progress-hero.jpg)</span></span><br>
<span data-ttu-id="38e11-108">*Exemplo de anel de progresso no HoloLens*</span><span class="sxs-lookup"><span data-stu-id="38e11-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="38e11-109">Tipo de progresso</span><span class="sxs-lookup"><span data-stu-id="38e11-109">Types of progress</span></span>

<span data-ttu-id="38e11-110">É importante fornecer as informações do usuário sobre o que está acontecendo.</span><span class="sxs-lookup"><span data-stu-id="38e11-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="38e11-111">Na realidade mista que os usuários podem ser facilmente Distraídos com ambiente físico ou objetos se seu aplicativo não dá bons comentários visuais.</span><span class="sxs-lookup"><span data-stu-id="38e11-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="38e11-112">Para situações que levam alguns segundos, como quando o carregamento de dados ou uma cena está atualizando, é recomendável para mostrar um indicador visual.</span><span class="sxs-lookup"><span data-stu-id="38e11-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="38e11-113">Há duas opções para mostrar ao usuário que uma operação está em andamento – uma **barra de progresso** ou um **anel de progresso**.</span><span class="sxs-lookup"><span data-stu-id="38e11-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="38e11-114">Barra de progresso</span><span class="sxs-lookup"><span data-stu-id="38e11-114">Progress bar</span></span>

![Exemplo de barra de progresso no HoloLens](images/640px-progressbar.jpg)

<span data-ttu-id="38e11-116">Uma barra de progresso mostra o percentual da conclusão de uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="38e11-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="38e11-117">Ele deve ser usado durante uma operação cuja duração é conhecida (determinada), mas seu andamento não deve bloquear a interação do usuário com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="38e11-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="38e11-118">Anel de progresso</span><span class="sxs-lookup"><span data-stu-id="38e11-118">Progress ring</span></span>

![Exemplo de anel de progresso no HoloLens](images/640px-progressring.jpg)

<span data-ttu-id="38e11-120">Apenas um anel de progresso tem um estado indeterminado e deve ser usado quando qualquer interação adicional do usuário é bloqueada até que a operação foi concluída.</span><span class="sxs-lookup"><span data-stu-id="38e11-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="38e11-121">Progresso com um objeto personalizado</span><span class="sxs-lookup"><span data-stu-id="38e11-121">Progress with a custom object</span></span>

![Progresso com exemplo de malha personalizadas HoloLens](images/640px-progresscustom.jpg)

<span data-ttu-id="38e11-123">Você pode adicionar a personalidade e uma identidade visual do seu aplicativo, personalizando o controle de progresso com seus próprios objetos 2D/3D personalizados.</span><span class="sxs-lookup"><span data-stu-id="38e11-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="38e11-124">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="38e11-124">Best practices</span></span>
* <span data-ttu-id="38e11-125">Acoplar rigidamente [billboarding ou tag-along](billboarding-and-tag-along.md) para a exibição do progresso, pois o usuário pode facilmente mover suas cabeças no espaço vazio e perder o contexto.</span><span class="sxs-lookup"><span data-stu-id="38e11-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="38e11-126">Seu aplicativo pode parecer falhou se o usuário não conseguir ver nada.</span><span class="sxs-lookup"><span data-stu-id="38e11-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="38e11-127">Billboarding e tag-along é incorporada no pré-fabricado progresso.</span><span class="sxs-lookup"><span data-stu-id="38e11-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="38e11-128">É sempre bom fornecer informações de status sobre o que está acontecendo para o usuário.</span><span class="sxs-lookup"><span data-stu-id="38e11-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="38e11-129">Pré-fabricado andamento fornece diversos estilos visuais, incluindo o progresso de padrão de tipo de anel do Windows para fornecer o status.</span><span class="sxs-lookup"><span data-stu-id="38e11-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="38e11-130">Você também pode usar uma malha personalizada com uma animação, se você deseja que o estilo de seu progresso para alinhar à marca do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="38e11-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="38e11-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38e11-131">See also</span></span>
* [<span data-ttu-id="38e11-132">Pré-fabricados para o progresso no Kit de ferramentas de realidade mista e scripts</span><span class="sxs-lookup"><span data-stu-id="38e11-132">Scripts and prefabs for Progress on Mixed Reality Toolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ProgressExample.md)
* [<span data-ttu-id="38e11-133">Objeto interagível</span><span class="sxs-lookup"><span data-stu-id="38e11-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="38e11-134">Coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="38e11-134">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="38e11-135">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="38e11-135">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)

---
title: Focar
description: Olhar é o primeiro formulário de entrada e um formulário principal de direcionamento de dentro de realidade misturada.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Misto realidade, olhar, interação, de design
ms.openlocfilehash: 9e50067f9dfeacf3dce5ea9a928990d1b142e4d0
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453711"
---
# <a name="gaze"></a><span data-ttu-id="2b8cf-104">Focar</span><span class="sxs-lookup"><span data-stu-id="2b8cf-104">Gaze</span></span>

<span data-ttu-id="2b8cf-105">**Mantenha o foco** é o primeiro formulário de entrada e é uma forma principal de direcionamento dentro de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="2b8cf-106">Olhar informa onde o usuário está procurando no mundo e permite que você determine sua intenção.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="2b8cf-107">No mundo real, você geralmente verá um objeto que você pretende interagir com.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="2b8cf-108">Isso é o mesmo com olhar.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-108">This is the same with gaze.</span></span>

<span data-ttu-id="2b8cf-109">Realidade misturada headsets usarem a posição e orientação da cabeça do usuário para determinar seu vetor olhar principal.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="2b8cf-110">Você pode pensar esse vetor como um ponteiro a laser diretamente para frente da diretamente entre a atenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="2b8cf-111">Como o usuário procura ao redor de sala, seu aplicativo pode se cruzar essa ray com seus próprio hologramas e com o [mapeamento espacial](spatial-mapping.md) malha para determinar que o usuário pode estar olhando de objeto reais ou virtual.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="2b8cf-112">Em 2 HoloLens, interações podem ser alvo de olhar de principal do usuário, olhar olho ou por meio de perto ou muito entregar as interações.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="2b8cf-113">No HoloLens (1º gen), as interações geralmente devem derivar seu direcionamento de olhar de principal do usuário, em vez de tentar renderizar ou interagir diretamente no local da mão.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="2b8cf-114">Após o início de uma interação relativos movimentos da mão podem ser usado para controlar a [gesto](gestures.md), assim como acontece com as [manipulação ou navegação](gestures.md#composite-gestures) gesto.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="2b8cf-115">Com fones imersivos em exposição, você pode direcionar usando qualquer um dos olhar principal ou compatíveis com apontando [controladores de movimento](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="2b8cf-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="2b8cf-116">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="2b8cf-116">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="2b8cf-117">Recurso</span><span class="sxs-lookup"><span data-stu-id="2b8cf-117">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="2b8cf-118"><a href="hololens-hardware-details.md">HoloLens (1ª geração)</a></span><span class="sxs-lookup"><span data-stu-id="2b8cf-118"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="2b8cf-119">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2b8cf-119">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="2b8cf-120"><a href="immersive-headset-hardware-details.md">Fones imersivos em exposição</a></span><span class="sxs-lookup"><span data-stu-id="2b8cf-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="2b8cf-121">Mantenha o foco principal</span><span class="sxs-lookup"><span data-stu-id="2b8cf-121">Head gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="2b8cf-122">✔️</span><span class="sxs-lookup"><span data-stu-id="2b8cf-122">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="2b8cf-123">✔️</span><span class="sxs-lookup"><span data-stu-id="2b8cf-123">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="2b8cf-124">✔️</span><span class="sxs-lookup"><span data-stu-id="2b8cf-124">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2b8cf-125">Olhar olho</span><span class="sxs-lookup"><span data-stu-id="2b8cf-125">Eye gaze</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="2b8cf-126">✔️</span><span class="sxs-lookup"><span data-stu-id="2b8cf-126">✔️</span></span></td><td></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="2b8cf-127">Mais orientações específicas para 2 HoloLens [em breve](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="2b8cf-127">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="2b8cf-128">Usos de olhar</span><span class="sxs-lookup"><span data-stu-id="2b8cf-128">Uses of gaze</span></span>

<span data-ttu-id="2b8cf-129">Como um desenvolvedor de realidade misturada, você pode fazer muito com olhar head ou olhos:</span><span class="sxs-lookup"><span data-stu-id="2b8cf-129">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="2b8cf-130">Seu aplicativo pode se cruzar olhar com os hologramas na sua cena para determinar onde está a atenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-130">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="2b8cf-131">Seu aplicativo pode direcionar gestos e pressionamentos de controlador com base em olhar do usuário, permitindo que o usuário selecione, ativar, pegue, role ou caso contrário, interagir com seus hologramas.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-131">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="2b8cf-132">Seu aplicativo pode permitir que o usuário coloque hologramas em superfícies do mundo real, por meio de interseção seu ray olhar com a malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-132">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="2b8cf-133">Seu aplicativo possa saber quando o usuário estiver *não* procurando na direção de um objeto importante, que pode levar seu aplicativo para dar indicações de áudio e vídeo para ativar em direção esse objeto.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-133">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="2b8cf-134">Cursor</span><span class="sxs-lookup"><span data-stu-id="2b8cf-134">Cursor</span></span>

<span data-ttu-id="2b8cf-135">Para olhar principal, a maioria dos aplicativos deve usar um [cursor](cursors.md) (ou outra indicação auditivo/visual) para dar a confiança do usuário no que está prestes a interagir com.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-135">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="2b8cf-136">Você normalmente posicionar esse cursor no mundo onde seu ray olhar principal primeiro faz interseção com um objeto, que pode ser um holograma ou uma superfície do mundo real.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-136">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="2b8cf-137">![Um cursor visual de exemplo para mostrar a olhar](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="2b8cf-137">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="2b8cf-138">*Um cursor visual de exemplo para mostrar a olhar*</span><span class="sxs-lookup"><span data-stu-id="2b8cf-138">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="2b8cf-139">Para olhar olho, geralmente recomendamos *não* para mostrar um cursor, pois isso pode rapidamente se tornar causa distração e irritante do usuário.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-139">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="2b8cf-140">Em vez disso, um pouco realce visual destinos ou usar um cursor muito fraco olho para fornecer confiança sobre o que o usuário está prestes a interagir com.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-140">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="2b8cf-141">Para obter mais informações, Confira nossos [diretrizes de design para a entrada baseada em olho](eye-tracking.md) em HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-141">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="2b8cf-142">Dando a ação para olhar do usuário</span><span class="sxs-lookup"><span data-stu-id="2b8cf-142">Giving action to the user's gaze</span></span>

<span data-ttu-id="2b8cf-143">Depois que o usuário direcionou um holograma ou o objeto real usando seu olhar, sua próxima etapa é executar ação no objeto.</span><span class="sxs-lookup"><span data-stu-id="2b8cf-143">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="2b8cf-144">As formas básicas para um usuário tomar medidas são feitas por meio [gestos](gestures.md), [controladores de movimento](motion-controllers.md) e [voz](voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="2b8cf-144">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b8cf-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b8cf-145">See also</span></span>
* [<span data-ttu-id="2b8cf-146">Entrada do MR 210: Mantenha o foco principal</span><span class="sxs-lookup"><span data-stu-id="2b8cf-146">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="2b8cf-147">Olhar fixo com cabeça e olhos no DirectX</span><span class="sxs-lookup"><span data-stu-id="2b8cf-147">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="2b8cf-148">Head olhar no Unity</span><span class="sxs-lookup"><span data-stu-id="2b8cf-148">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="2b8cf-149">Acompanhamento em HoloLens 2 a olho nu</span><span class="sxs-lookup"><span data-stu-id="2b8cf-149">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="2b8cf-150">Olhar de olho no Unity usando o Kit de ferramentas de realidade mista</span><span class="sxs-lookup"><span data-stu-id="2b8cf-150">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)

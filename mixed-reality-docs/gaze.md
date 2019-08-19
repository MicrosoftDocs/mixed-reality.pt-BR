---
title: Focar
description: Olhar é a primeira forma de entrada e é uma forma primária de direcionamento dentro de realidade misturada.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Realidade misturada, olhar, interação, design
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414375"
---
# <a name="gaze"></a><span data-ttu-id="7e9b6-104">Focar</span><span class="sxs-lookup"><span data-stu-id="7e9b6-104">Gaze</span></span>

<span data-ttu-id="7e9b6-105">**Olhar** é a primeira forma de entrada e é uma forma primária de direcionamento dentro de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="7e9b6-106">O olhar informa o que o usuário está procurando no mundo e permite que você determine sua intenção.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="7e9b6-107">No mundo real, você normalmente examinará um objeto com o qual você pretende interagir.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="7e9b6-108">Isso é o mesmo com olhar.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-108">This is the same with gaze.</span></span>

<span data-ttu-id="7e9b6-109">Os headsets de realidade misturada usam a posição e a orientação da cabeça do usuário para determinar o vetor olhar de cabeça.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="7e9b6-110">Você pode considerar esse vetor como um ponteiro laser diretamente entre os olhos do usuário.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="7e9b6-111">À medida que o usuário olha pela sala, seu aplicativo pode Interseccionar esse raio, ambos com seus próprios hologramas e com a malha de [mapeamento espacial](spatial-mapping.md) para determinar qual objeto virtual ou real seu usuário pode estar olhando.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="7e9b6-112">No HoloLens 2, as interações podem ser direcionadas pela cabeça do usuário olhar, olho olhar ou pelas interações de perto ou longe da mão.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="7e9b6-113">No HoloLens (1º gen), as interações geralmente devem derivar seu direcionamento do olhar de cabeça do usuário, em vez de tentar renderizar ou interagir diretamente no local da mão.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="7e9b6-114">Depois que uma interação for iniciada, movimentos relativos da mão poderão ser usados para controlar o [gesto](gestures.md), assim como com o gesto de [manipulação ou de navegação](gestures.md#composite-gestures) .</span><span class="sxs-lookup"><span data-stu-id="7e9b6-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="7e9b6-115">Com headsets de imersão, você pode direcionar usando olhar de cabeça ou [controladores de movimento](motion-controllers.md)com capacidade de apontamento.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="7e9b6-116">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="7e9b6-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7e9b6-117"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="7e9b6-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="7e9b6-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e9b6-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7e9b6-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="7e9b6-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="7e9b6-120"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="7e9b6-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e9b6-121">Olhar de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="7e9b6-121">Head gaze</span></span></td>
        <td><span data-ttu-id="7e9b6-122">✔️</span><span class="sxs-lookup"><span data-stu-id="7e9b6-122">✔️</span></span></td>
        <td><span data-ttu-id="7e9b6-123">✔️</span><span class="sxs-lookup"><span data-stu-id="7e9b6-123">✔️</span></span></td>
        <td><span data-ttu-id="7e9b6-124">✔️</span><span class="sxs-lookup"><span data-stu-id="7e9b6-124">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7e9b6-125">Olhar de olho</span><span class="sxs-lookup"><span data-stu-id="7e9b6-125">Eye gaze</span></span></td>
        <td><span data-ttu-id="7e9b6-126">❌</span><span class="sxs-lookup"><span data-stu-id="7e9b6-126">❌</span></span></td>
        <td><span data-ttu-id="7e9b6-127">✔️</span><span class="sxs-lookup"><span data-stu-id="7e9b6-127">✔️</span></span></td>
        <td><span data-ttu-id="7e9b6-128">❌</span><span class="sxs-lookup"><span data-stu-id="7e9b6-128">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="7e9b6-129">Mais diretrizes específicas para o HoloLens 2 em [breve](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="7e9b6-129">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="7e9b6-130">Usos de olhar</span><span class="sxs-lookup"><span data-stu-id="7e9b6-130">Uses of gaze</span></span>

<span data-ttu-id="7e9b6-131">Como um desenvolvedor de realidade misturada, você pode fazer muito com olhar de cabeça ou olho:</span><span class="sxs-lookup"><span data-stu-id="7e9b6-131">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="7e9b6-132">Seu aplicativo pode Interseccionar olhar com os hologramas em sua cena para determinar onde está a atenção do usuário.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-132">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="7e9b6-133">Seu aplicativo pode direcionar gestos e pressionamentos de controlador com base no olhar do usuário, permitindo que o usuário selecione, ative, pegue, role ou, de outra forma, interaja com seus hologramas.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-133">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="7e9b6-134">Seu aplicativo pode permitir que o usuário Coloque os hologramas em superfícies do mundo real, interseccionando seu olhar Ray com a malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-134">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="7e9b6-135">Seu aplicativo pode saber quando o usuário *não* está olhando para a direção de um objeto importante, o que pode levar seu aplicativo a dar indicações visuais e de áudio para virar esse objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-135">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="7e9b6-136">Cursor</span><span class="sxs-lookup"><span data-stu-id="7e9b6-136">Cursor</span></span>

<span data-ttu-id="7e9b6-137">Para o Head olhar, a maioria dos aplicativos deve usar um [cursor](cursors.md) (ou outra indicação de auditoria/Visual) para dar ao usuário a confiança no que eles estão prestes a interagir.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-137">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="7e9b6-138">Normalmente, você posiciona esse cursor no mundo em que o Head olhar Ray primeiro cruza um objeto, que pode ser um holograma ou uma superfície do mundo real.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-138">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="7e9b6-139">![Um cursor visual de exemplo para mostrar olhar](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="7e9b6-139">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="7e9b6-140">*Um cursor visual de exemplo para mostrar olhar*</span><span class="sxs-lookup"><span data-stu-id="7e9b6-140">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="7e9b6-141">Para olhar de olho, geralmente recomendamos *não* mostrar um cursor, pois isso pode rapidamente se tornar confuso e irritante para o usuário.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-141">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="7e9b6-142">Em vez disso, destaque sutilmente os destinos visuais ou use um cursor de olho muito fraco para fornecer confiança sobre o que o usuário está prestes a interagir.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-142">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="7e9b6-143">Para obter mais informações, confira nossas [diretrizes de design para entrada baseada em olhos](eye-tracking.md) no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-143">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="7e9b6-144">Dando ação ao olhar do usuário</span><span class="sxs-lookup"><span data-stu-id="7e9b6-144">Giving action to the user's gaze</span></span>

<span data-ttu-id="7e9b6-145">Depois que o usuário tiver direcionado um holograma ou um objeto do mundo real usando seus olhar, a próxima etapa será executar uma ação nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9b6-145">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="7e9b6-146">As principais maneiras de um usuário executar ações são por meio de [gestos](gestures.md), [controladores de movimento](motion-controllers.md) e [voz](voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="7e9b6-146">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e9b6-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e9b6-147">See also</span></span>
* [<span data-ttu-id="7e9b6-148">Entrada do MR 210: Olhar de cabeçalho</span><span class="sxs-lookup"><span data-stu-id="7e9b6-148">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="7e9b6-149">Olhar fixo com cabeça e olhos no DirectX</span><span class="sxs-lookup"><span data-stu-id="7e9b6-149">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="7e9b6-150">Olhar de cabeçalho no Unity</span><span class="sxs-lookup"><span data-stu-id="7e9b6-150">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="7e9b6-151">Olho-olhar no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7e9b6-151">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="7e9b6-152">Olho olhar no Unity usando o kit de ferramentas da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="7e9b6-152">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)

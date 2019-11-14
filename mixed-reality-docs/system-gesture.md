---
title: Gesto do sistema
description: Gesto do sistema para chamar o menu iniciar.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realidade misturada, gestos, interação, design
ms.openlocfilehash: 417811fff9d98e459dc0047d46ea065acfced4ef
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064235"
---
# <a name="system-gesture"></a><span data-ttu-id="208a8-104">Gesto do sistema</span><span class="sxs-lookup"><span data-stu-id="208a8-104">System gesture</span></span>

<span data-ttu-id="208a8-105">O gesto do sistema é um gesto de mão usado para invocar o menu iniciar.</span><span class="sxs-lookup"><span data-stu-id="208a8-105">The system gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="208a8-106">É o equivalente a pressionar a tecla Windows no teclado, o botão Xbox em um controlador Xbox ou o botão Windows no controlador de movimento de headsets de imersão.</span><span class="sxs-lookup"><span data-stu-id="208a8-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="208a8-107">É importante entender quais gestos são reservados para o sistema em cada dispositivo de realidade misturada para evitar conflitos ao projetar suas interações.</span><span class="sxs-lookup"><span data-stu-id="208a8-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="208a8-108">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="208a8-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="208a8-109"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="208a8-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="208a8-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="208a8-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="208a8-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="208a8-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="208a8-112"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="208a8-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="208a8-113">Cair</span><span class="sxs-lookup"><span data-stu-id="208a8-113">Bloom</span></span></td>
        <td><span data-ttu-id="208a8-114">✔️</span><span class="sxs-lookup"><span data-stu-id="208a8-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="208a8-115">Botão do pulso</span><span class="sxs-lookup"><span data-stu-id="208a8-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="208a8-116">✔️</span><span class="sxs-lookup"><span data-stu-id="208a8-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="208a8-117">Olho olhar e Palm up pinçar</span><span class="sxs-lookup"><span data-stu-id="208a8-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="208a8-118">✔️</span><span class="sxs-lookup"><span data-stu-id="208a8-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="208a8-119">Cair</span><span class="sxs-lookup"><span data-stu-id="208a8-119">Bloom</span></span>
<span data-ttu-id="208a8-120">Para abrir o menu iniciar no HoloLens (1º gen), projetamos "flor", que é um gesto simbólico imitando Blossom de flor.</span><span class="sxs-lookup"><span data-stu-id="208a8-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="208a8-121">É distintivo para a interação Surefooted, fácil de executar e rápida de se recuperar.</span><span class="sxs-lookup"><span data-stu-id="208a8-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="208a8-122">Para fazer o gesto de cair no HoloLens (1º gen), mantenha sua mão em dia com seu Palm para cima e, em seguida, abra sua mão distribuindo os dedos.</span><span class="sxs-lookup"><span data-stu-id="208a8-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="208a8-123">![de cair perto](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="208a8-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="208a8-124">**Etapa 1: Palm juntos**</span><span class="sxs-lookup"><span data-stu-id="208a8-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="208a8-125">![abertura](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="208a8-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="208a8-126">**Etapa 2: Palm up com as mãos espalhadas**</span><span class="sxs-lookup"><span data-stu-id="208a8-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a><span data-ttu-id="208a8-127">Botão do pulso</span><span class="sxs-lookup"><span data-stu-id="208a8-127">Wrist button</span></span>
<span data-ttu-id="208a8-128">No HoloLens 2, substituímos o gesto de cair com um botão de pulso virtual que permite interações mais instinctuals que não exigem ensino adicional.</span><span class="sxs-lookup"><span data-stu-id="208a8-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="208a8-129">Ao mostrar os usuários o botão no pulso, eles podem acessá-lo intuitivamente e pressioná-lo com a outra mão.</span><span class="sxs-lookup"><span data-stu-id="208a8-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="208a8-130">![botão do punho pronto](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="208a8-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="208a8-131">**Etapa 1: Palm up para mostrar o botão do pulso**</span><span class="sxs-lookup"><span data-stu-id="208a8-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="208a8-132">![pressionar o botão do pulso](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="208a8-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="208a8-133">**Etapa 2: Pressione o botão do pulso**</span><span class="sxs-lookup"><span data-stu-id="208a8-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a><span data-ttu-id="208a8-134">Olho-olhar e Palm up pinçar</span><span class="sxs-lookup"><span data-stu-id="208a8-134">Eye-gaze and palm up pinch</span></span>
<span data-ttu-id="208a8-135">Também projetamos uma solução única para facilitar o acesso no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="208a8-135">We have also designed a one-handed solution for ease of access in HoloLens 2.</span></span> <span data-ttu-id="208a8-136">Esse gesto exige que os usuários olho olhar no botão do pulso e, em seguida, usam a mesma mão para realizar uma pinçagem para cima usando seu polegar e um dedo de índice.</span><span class="sxs-lookup"><span data-stu-id="208a8-136">This gesture requires users to eye gaze at the wrist button, then use the same hand to perform a palm up pinch using their thumb and index finger.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="208a8-137">![botão do punho pronto](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="208a8-137">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="208a8-138">**Etapa 1: Palm up para mostrar o botão do pulso**</span><span class="sxs-lookup"><span data-stu-id="208a8-138">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="208a8-139">![botão do pulso de pinçagem](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="208a8-139">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="208a8-140">**Etapa 2: olho olhar no botão e, em seguida, aperte**</span><span class="sxs-lookup"><span data-stu-id="208a8-140">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="208a8-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="208a8-141">See also</span></span>

* [<span data-ttu-id="208a8-142">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="208a8-142">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="208a8-143">Olhar fixo</span><span class="sxs-lookup"><span data-stu-id="208a8-143">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="208a8-144">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="208a8-144">Voice input</span></span>](voice-input.md)

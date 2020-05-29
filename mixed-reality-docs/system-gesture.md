---
title: Iniciar gesto
description: Iniciar gesto para chamar o menu iniciar.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realidade misturada, gestos, interação, design
ms.openlocfilehash: 84088156d0c9cdacc421985b922d5e9370f6a87e
ms.sourcegitcommit: fd606e87e3c4785d3ca2a26632be3bb580e39afb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84152519"
---
# <a name="start-gesture"></a><span data-ttu-id="20569-104">Iniciar gesto</span><span class="sxs-lookup"><span data-stu-id="20569-104">Start gesture</span></span>

<span data-ttu-id="20569-105">O gesto de início é um gesto de mão usado para invocar o menu iniciar.</span><span class="sxs-lookup"><span data-stu-id="20569-105">The Start gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="20569-106">É o equivalente a pressionar a tecla Windows no teclado, o botão Xbox em um controlador Xbox ou o botão Windows no controlador de movimento de headsets de imersão.</span><span class="sxs-lookup"><span data-stu-id="20569-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="20569-107">É importante entender quais gestos são reservados para o sistema em cada dispositivo de realidade misturada para evitar conflitos ao projetar suas interações.</span><span class="sxs-lookup"><span data-stu-id="20569-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="20569-108">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="20569-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="20569-109"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="20569-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="20569-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="20569-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="20569-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="20569-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="20569-112"><a href="immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="20569-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="20569-113">Bloom</span><span class="sxs-lookup"><span data-stu-id="20569-113">Bloom</span></span></td>
        <td><span data-ttu-id="20569-114">✔️</span><span class="sxs-lookup"><span data-stu-id="20569-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="20569-115">Botão do pulso</span><span class="sxs-lookup"><span data-stu-id="20569-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="20569-116">✔️</span><span class="sxs-lookup"><span data-stu-id="20569-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="20569-117">Olho olhar e Palm up pinçar</span><span class="sxs-lookup"><span data-stu-id="20569-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="20569-118">✔️</span><span class="sxs-lookup"><span data-stu-id="20569-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="20569-119">Bloom</span><span class="sxs-lookup"><span data-stu-id="20569-119">Bloom</span></span>
<span data-ttu-id="20569-120">Para abrir o menu iniciar no HoloLens (1º gen), projetamos "flor", que é um gesto simbólico imitando Blossom de flor.</span><span class="sxs-lookup"><span data-stu-id="20569-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="20569-121">É distintivo para a interação Surefooted, fácil de executar e rápida de se recuperar.</span><span class="sxs-lookup"><span data-stu-id="20569-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="20569-122">Para fazer o gesto de cair no HoloLens (1º gen), mantenha sua mão em dia com seu Palm para cima e, em seguida, abra sua mão distribuindo os dedos.</span><span class="sxs-lookup"><span data-stu-id="20569-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="20569-123">![Fechamento de flor](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="20569-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="20569-124">**Etapa 1: Palm juntos**</span><span class="sxs-lookup"><span data-stu-id="20569-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="20569-125">![Flor aberta](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="20569-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="20569-126">**Etapa 2: Palm up com as mãos espalhadas**</span><span class="sxs-lookup"><span data-stu-id="20569-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="20569-127">Iniciar gesto</span><span class="sxs-lookup"><span data-stu-id="20569-127">Start gesture</span></span>
<span data-ttu-id="20569-128">No HoloLens 2, substituímos o gesto de cair com um botão de pulso virtual que permite interações mais instinctuals que não exigem ensino adicional.</span><span class="sxs-lookup"><span data-stu-id="20569-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="20569-129">Ao mostrar os usuários o botão no pulso, eles podem acessá-lo intuitivamente e pressioná-lo com a outra mão.</span><span class="sxs-lookup"><span data-stu-id="20569-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="20569-130">![Botão do punho pronto](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="20569-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="20569-131">**Etapa 1: Palm up para mostrar o botão do pulso**</span><span class="sxs-lookup"><span data-stu-id="20569-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="20569-132">![Botão do pulso pressionado](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="20569-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="20569-133">**Etapa 2: Pressione o botão do pulso**</span><span class="sxs-lookup"><span data-stu-id="20569-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a><span data-ttu-id="20569-134">Gesto de início de uma mão</span><span class="sxs-lookup"><span data-stu-id="20569-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20569-135">Para que o gesto de início de uma mão funcione:</span><span class="sxs-lookup"><span data-stu-id="20569-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="20569-136">Você deve atualizar para a atualização de novembro de 2019 (Build 18363,1039) ou posterior.</span><span class="sxs-lookup"><span data-stu-id="20569-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="20569-137">Seus olhos devem ser calibrados no dispositivo para que o acompanhamento de olho funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="20569-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="20569-138">Se você não vir pontos de an-órbita em volta do ícone iniciar quando olhar para ele, seus olhos não serão calibrados no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="20569-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="20569-139">Você também pode executar o gesto de início com apenas uma mão.</span><span class="sxs-lookup"><span data-stu-id="20569-139">You can also perform the Start gesture with only one hand.</span></span> <span data-ttu-id="20569-140">Para fazer isso, mantenha sua mão com seu Palm e veja o **ícone iniciar** no pulso interno.</span><span class="sxs-lookup"><span data-stu-id="20569-140">To do this, hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="20569-141">**Enquanto mantém seu olho no ícone**, aperte seu polegar e indexe o dedo em conjunto.</span><span class="sxs-lookup"><span data-stu-id="20569-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="20569-142">![Botão do punho pronto](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="20569-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="20569-143">**Etapa 1: Palm up para mostrar o botão do pulso**</span><span class="sxs-lookup"><span data-stu-id="20569-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="20569-144">![Botão do pulso pinçar](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="20569-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="20569-145">**Etapa 2: olho olhar no botão e, em seguida, aperte**</span><span class="sxs-lookup"><span data-stu-id="20569-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="20569-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="20569-146">See also</span></span>

* [<span data-ttu-id="20569-147">Interações instinctuais</span><span class="sxs-lookup"><span data-stu-id="20569-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="20569-148">Olho-olhar</span><span class="sxs-lookup"><span data-stu-id="20569-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="20569-149">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="20569-149">Voice input</span></span>](voice-input.md)

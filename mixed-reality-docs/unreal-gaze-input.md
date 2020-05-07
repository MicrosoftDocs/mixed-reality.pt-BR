---
title: Entrada olhar em não real
description: Explica como usar a entrada olhar em um modo inreal
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Realidade mista do Windows, hologramas, HoloLens, acompanhamento de olho
ms.openlocfilehash: 7387bb3f25cdbdfac32f508c173fbd098f844e84
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835615"
---
# <a name="gaze-input"></a><span data-ttu-id="00182-104">Entrada olhar</span><span class="sxs-lookup"><span data-stu-id="00182-104">Gaze Input</span></span>

<span data-ttu-id="00182-105">O plug-in de realidade mista do Windows não fornece nenhuma função especial para a entrada olhar.</span><span class="sxs-lookup"><span data-stu-id="00182-105">The Windows Mixed Reality plugin doesn’t provide any special functions for the gaze input.</span></span> <span data-ttu-id="00182-106">Tudo funciona embora a API não real padrão.</span><span class="sxs-lookup"><span data-stu-id="00182-106">Everything works though the standard Unreal API.</span></span>

[<span data-ttu-id="00182-107">API do Head olhar</span><span class="sxs-lookup"><span data-stu-id="00182-107">Head gaze API</span></span>](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a><span data-ttu-id="00182-108">Acompanhamento ocular</span><span class="sxs-lookup"><span data-stu-id="00182-108">Eye tracking</span></span>

<span data-ttu-id="00182-109">Para usar a API de acompanhamento ocular, os desenvolvedores devem habilitar a funcionalidade de "entrada olhar" em suas configurações de projeto do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="00182-109">To use the eye tracking API, developers should enable the “Gaze Input” capability in their HoloLens project settings.</span></span> <span data-ttu-id="00182-110">Quando o aplicativo for iniciado, o usuário verá o seguinte prompt de consentimento</span><span class="sxs-lookup"><span data-stu-id="00182-110">When the application starts, user will see the following consent prompt</span></span>

![Permissões de entrada de olho](images/unreal/eye-input-permissions.png)
 
<span data-ttu-id="00182-112">Se o usuário der sua permissão, o aplicativo receberá uma entrada olhar.</span><span class="sxs-lookup"><span data-stu-id="00182-112">If the user gives their permission, the application will get eye gaze input.</span></span> 

<span data-ttu-id="00182-113">A API de acompanhamento de olho inreal está documentada [aqui](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)</span><span class="sxs-lookup"><span data-stu-id="00182-113">Unreal’s eye tracking API is documented is [here](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)</span></span>

<span data-ttu-id="00182-114">Os detalhes técnicos de acompanhamento de olho estão [aqui](eye-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="00182-114">The technical details of eye tracking are [here](eye-tracking.md)</span></span>

<span data-ttu-id="00182-115">Observe que, especificamente para o controle de olhos inreal, o HoloLens tem um único olhar Ray para ambos os olhos.</span><span class="sxs-lookup"><span data-stu-id="00182-115">Note that specifically for Unreal, HoloLens eye tracking has a single gaze ray for both eyes.</span></span> <span data-ttu-id="00182-116">O HoloLens não fornece controle ocular estereoscópico.</span><span class="sxs-lookup"><span data-stu-id="00182-116">HoloLens doesn’t provide stereoscopic eye tracking.</span></span>

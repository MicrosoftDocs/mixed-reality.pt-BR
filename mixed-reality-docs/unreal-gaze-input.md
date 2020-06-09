---
title: Entrada olhar em não real
description: Tutorial sobre como configurar a entrada de olhar para o HoloLens e o mecanismo inreal
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Realidade mista do Windows, hologramas, HoloLens 2, controle de olho, entrada olhar, tela de montagem de cabeça, mecanismo inreal
ms.openlocfilehash: 0bc8b83a2e840b066eb5e30665584e1c68f7b021
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84551802"
---
# <a name="gaze-input"></a><span data-ttu-id="a893b-104">Entrada olhar</span><span class="sxs-lookup"><span data-stu-id="a893b-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="a893b-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="a893b-105">Overview</span></span>

<span data-ttu-id="a893b-106">O [plug-in do Windows Mixed Reality](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) não fornece funções internas para entrada olhar, mas o HoloLens 2 dá suporte ao acompanhamento de olho.</span><span class="sxs-lookup"><span data-stu-id="a893b-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="a893b-107">Os recursos de acompanhamento reais são fornecidos por APIs de exibição e acompanhamento de cabeça e de **controle de olhos** **desmontadas** e incluem:</span><span class="sxs-lookup"><span data-stu-id="a893b-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="a893b-108">Informações do dispositivo</span><span class="sxs-lookup"><span data-stu-id="a893b-108">Device information</span></span>
- <span data-ttu-id="a893b-109">Sensores de acompanhamento</span><span class="sxs-lookup"><span data-stu-id="a893b-109">Tracking sensors</span></span>
- <span data-ttu-id="a893b-110">Orientação e posição</span><span class="sxs-lookup"><span data-stu-id="a893b-110">Orientation and position</span></span>
- <span data-ttu-id="a893b-111">Painéis de recorte</span><span class="sxs-lookup"><span data-stu-id="a893b-111">Clipping panes</span></span>
- <span data-ttu-id="a893b-112">Informações de rastreamento e dados do olhar</span><span class="sxs-lookup"><span data-stu-id="a893b-112">Gaze data and tracking information</span></span>

<span data-ttu-id="a893b-113">Você pode encontrar a lista completa de recursos na documentação de exibição e [controle de olho](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) do [rumo](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) .</span><span class="sxs-lookup"><span data-stu-id="a893b-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="a893b-114">Além das APIs inreais, confira a documentação sobre a [interação baseada em olhar](eye-gaze-interaction.md) para o hololens 2 e leia como o [controle de olhos no hololens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) funciona.</span><span class="sxs-lookup"><span data-stu-id="a893b-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a893b-115">Só há suporte para acompanhamento de olho no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a893b-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="a893b-116">Habilitando o acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="a893b-116">Enabling eye tracking</span></span>
<span data-ttu-id="a893b-117">A entrada olhar precisa ser habilitada nas configurações do projeto do HoloLens antes que você possa usar qualquer uma das APIs inreais.</span><span class="sxs-lookup"><span data-stu-id="a893b-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="a893b-118">Quando o aplicativo for iniciado, você verá um prompt de consentimento mostrado na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="a893b-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="a893b-119">Selecione **Sim** para definir a permissão e obter acesso à entrada olhar.</span><span class="sxs-lookup"><span data-stu-id="a893b-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="a893b-120">Se você precisar alterar essa configuração a qualquer momento, ela poderá ser encontrada no aplicativo **configurações** .</span><span class="sxs-lookup"><span data-stu-id="a893b-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![Permissões de entrada de olho](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="a893b-122">O controle de olhos do HoloLens em tempo inreal tem apenas um único olhar Ray para ambos os olhos, em vez dos dois raios necessários para o acompanhamento do estereoscópico, o que não é suportado.</span><span class="sxs-lookup"><span data-stu-id="a893b-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="a893b-123">Essa é a configuração que você precisará para começar a adicionar a entrada olhar aos seus aplicativos do HoloLens 2 em um não real.</span><span class="sxs-lookup"><span data-stu-id="a893b-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="a893b-124">Mais informações sobre a entrada do olhar e como isso afeta os usuários em realidade misturada podem ser encontradas nos links abaixo.</span><span class="sxs-lookup"><span data-stu-id="a893b-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="a893b-125">Lembre-se de pensar nisso ao criar suas experiências interativas.</span><span class="sxs-lookup"><span data-stu-id="a893b-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="see-also"></a><span data-ttu-id="a893b-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a893b-126">See also</span></span>
* [<span data-ttu-id="a893b-127">Calibragem</span><span class="sxs-lookup"><span data-stu-id="a893b-127">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="a893b-128">Conforto</span><span class="sxs-lookup"><span data-stu-id="a893b-128">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="a893b-129">Focar e confirmar</span><span class="sxs-lookup"><span data-stu-id="a893b-129">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="a893b-130">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="a893b-130">Voice input</span></span>](voice-design.md)
